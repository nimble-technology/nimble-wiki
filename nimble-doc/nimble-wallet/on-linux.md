# On Linux

### Install Golang

* Open a terminal
* Execute the following commands
  * `sudo apt update`
  * `sudo apt install golang`
  * `export GOPATH=$HOME/go`
  * `export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`
  * `go version`

It should display the go version.

### Create Wallet

Note: Git is required for the remaining setup steps.

* Open a terminal
* Execute the following commands to download wallet CLI
  * `mkdir $HOME/nimble && cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/wallet-public.git`
  * `cd wallet-public`
  * `make install`
* Locate this executable command and confirm it exists
  * `nimble-networkd`
*   Execute the following command to create your wallet. Give your wallet a name, such as 'ilovenimble'.

    * `nimble-networkd keys add ilovenimble`
    * `(Type your passphrase)`
    * `(Save the seed phrase somewhere safe)`&#x20;



The “address: nimblexxxx” output means your Nimble Network wallet address was created successfully!

## Congrats 😘

You are now mining NIM!

For assistance, find us in our Discord server - [https://discord.gg/nimble](https://discord.gg/nimble)
