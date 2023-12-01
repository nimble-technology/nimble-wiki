---
description: Get started with intents
---

# Quickstart

### Installation

Install with npm or yarn&#x20;

```
npm i nimble-intents-sdk
```

```
yarn add nimble-intents-sdk
```

### Usage

This example demonstrates how to create an intent and submit it to our API server

```
const provider = new ethers.JsonRpcProvider(RPC_URL);
    // config entry point address and chain id for the sdk
    configure(ENTRY_POINT_ADDRESS, CHAIN_ID);
    // alice is the user who creates intent
    const alice = new ethers.Wallet(privateKey, provider);
    const bob = '0x23618e81E3f5cdF7f54C3d65f7FBc0aBf5B21E8f';
    const anthony = '0xa0Ee7A142d267C1f36714E4a8F75612F20a79720';


    const DAI: GeneralAssetStruct = { assetType: 1, assetAddress: "0x6b175474e89094c44da98b954eedeac495271d0f", assetId: 0 };
    const USDC: GeneralAssetStruct = { assetType: 1, assetAddress: '0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48', assetId: 0 };


    const releaseAmount = ethers.parseUnits("101", 18);
    const bobReceiveAmount = ethers.parseUnits("30", 18);
    const anthonyReceiveAmount = ethers.parseUnits("70", 6);


    // approve entryPoint to spend DAI
    const tokenABI = [
        {
            constant: false,
            inputs: [
                {
                    name: "_spender",
                    type: "address",
                },
                {
                    name: "_value",
                    type: "uint256",
                },
            ],
            name: "approve",
            outputs: [
                {
                    name: "",
                    type: "bool",
                },
            ],
            payable: false,
            stateMutability: "nonpayable",
            type: "function",
        },
    ];


    const tokenAddress = await resolveAddress(DAI.assetAddress);
    const tokenContract = new ethers.Contract(tokenAddress, tokenABI, alice);
    const txApprove = await tokenContract.approve(ENTRY_POINT_ADDRESS, releaseAmount);
    await txApprove.wait();


    // compose the checker field of the intent
    // this checker means that:
    //   1. alice will release 101 DAI to fulfill his intent at most
    //   2. bob will receive 30 DAI exactly
    //   3. anthony will receive 70 USDC exactly
    //   4. left DAI will be returned to alice
    const checker: TokenDeltasCheckerStruct = {
        deltas: [
            {
                token: DAI,
                account: alice,
                compare: 3, // 0: <, 1: <=, 2: >, 3: >=, 4: ==, 5: !=
                deltaAmount: releaseAmount * -1n,
            },
            {
                token: DAI,
                account: bob,
                compare: 4, // 0: <, 1: <=, 2: >, 3: >=, 4: ==, 5: !=
                deltaAmount: bobReceiveAmount,
            },
            {
              token: USDC,
              account: anthony,
              compare: 4, // 0: <, 1: <=, 2: >, 3: >=, 4: ==, 5: !=
              deltaAmount: anthonyReceiveAmount,
            }
        ]
    };
    // another checker example:
    //   1. alice will release 101 DAI to fullfill his intent
    //   2. bob will receive 30 DAI exactly
    //   3. anthony will receive 70 USDC at least
    const _checker2: TokenDeltasCheckerStruct = {
        deltas: [
            {
                token: DAI,
                account: alice,
                compare: 4, // 0: <, 1: <=, 2: >, 3: >=, 4: ==, 5: !=
                deltaAmount: releaseAmount * -1n,
            },
            {
                token: DAI,
                account: bob,
                compare: 4, // 0: <, 1: <=, 2: >, 3: >=, 4: ==, 5: !=
                deltaAmount: bobReceiveAmount,
            },
            {
                token: USDC,
                account: anthony,
                compare: 3, // 0: <, 1: <=, 2: >, 3: >=, 4: ==, 5: !=
                deltaAmount: anthonyReceiveAmount,
            }
        ]
    };


    const entryPoint = EntryPoint__factory.connect(ENTRY_POINT_ADDRESS, alice);
    const nonce = await entryPoint.getNonce(alice.address, 0);


    const intentOfAlice = await (new Intent({
        accountType: 0, // 0 for EOA wallet
        user: alice.address,
        timestamp: Math.floor(Date.now() / 1000),
        deadline: 0, // 0 means not expired
        nonce,
        releaser: [
            {
                token: DAI,
                to: ZeroAddress, // let solver decide where to send the tokens
                // maximum amount of tokens to be released; left amount will be returned to the user
                allowance: releaseAmount,
            },
        ],
        checker: Intent.abiEncodeChecker(checker),
        // empty intent handler id is to let the solver resolve which intent handler to use
        intentHandlerId: new Uint8Array(32),
    })).ethSign(alice);

    // send a POST request to nimble API to submit the intent via fetch
    const nimbleSolverAPI = 'https://api.test.nimble.technology/v1/intent';
    const response = await fetch(nimbleSolverAPI, {
        method: 'POST',
        headers: {
            'n-api-key': 'xxxxx', // api key is required for authentication
            "Content-Type": "application/json",
        },
        body: JSON.stringify(await intentOfAlice.toIntentDto())
    });
    const result = await response.json();
    console.log("result", result);
```

\
