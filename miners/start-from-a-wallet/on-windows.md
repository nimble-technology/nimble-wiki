# On Windows

### Install Golang

* Install Windows Subsystem for Linux (WSL)
  * [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)
* Nimble requires Go 1.22.1. If you already have a previous Go version installed, start by removing it
  * `sudo apt-get remove golang-go`
  * `sudo rm -rf /usr/local/go`
* Once completed, open a terminal and execute the following commands
  * `cd /usr/local`
  * `sudo wget https://go.dev/dl/go1.22.1.linux-amd64.tar.gz`
  * `sudo tar -C /usr/local -xzf go1.22.1.linux-amd64.tar.gz`
  * `export PATH=$PATH:/usr/local/go/bin`
  * `go version`

It should display the go version 1.22.1

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
* Execute the following command to create your wallet. Give your wallet a name, such as 'ilovenimble'.
  * `nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)`

The “address: nimblexxxx” output means your Nimble Network wallet address was created successfully!

## Congrats 😘

You are now mining NIM!

For assistance, find us in our Discord server - [https://discord.gg/nimble](https://discord.gg/nimble)
