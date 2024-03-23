---
description: A short guide to mining on Nimble
---

# Mining on Nimble

Use these instructions to configure your mining hardware and mine NIM.

Instructions are available for Linux, Windows 11, and Mac.

## System Specs

Recommended

* RTX 3090+ GPU
* Core i7 13700
* 16GB RAM
* 256 GB disk space

Minimum

* RTX 2080+ GPU (Linux/Windows), or M1/M2/M3 Mac chips
* Core i5 7400
* 16GB RAM
* 256 GB disk space

## Installing on Windows 11

### Install Golang

* Install Windows Subsystem for Linux (WSL)
  * [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)
* Once completed, open a terminal and execute the following commands
  * `sudo apt update`
  * `sudo apt install golang`
  * `export GOPATH=$HOME/go`
  * `export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`
  * `go version`

It should display the go version.

### Creat Wallet

Note: Git is required for the remaining setup steps.

* Open a terminal
* Execute the following commands to download wallet CLI
  * `mkdir $HOME/nimble && cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/wallet-public.git`
  * `cd wallet-public`
  * `make install`
* Locate this path and confirm it exists (replace \<you> with your username)
  * `/home/<you>/go/bin/nimble-networkd`
* Execute the following command to create your wallet. Give your wallet a name, such as 'ilovenimble'.
  * `[nimble-networkd path]/nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)`

The “address: nimblexxxx” output means your Nimble Network wallet address was created successfully!

### Start Mining

Note: python3.9 (or above) and pip3 are required for the remaining steps

* Open a terminal window
* Install python3 venv
  * `sudo apt update`
  * `sudo apt install python3-venv`

> If you encounter a failure while installing python3-venv, please execute the following commands.
>
> ```shell
> sudo apt-get install software-properties-common
> sudo add-apt-repository ppa:deadsnakes/ppa -y
> sudo apt install python3-venv
> ```

* Download and run nimble miner
  * `cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/nimble-miner-public.git`
  * `cd nimble-miner-public`
  * `make install`
  * `source ./nimenv_localminers/bin/activate`
  * `make run addr=<copy paste your “nimblexxx” wallet address here>`

To resume mining after your machine disconnects, re-run the command:

`make run addr=<copy paste your “nimblexxx” wallet address here>`

## Installing on Mac

### Install Golang

* Download and install Golang (**v1.22 or higher**)
  * [https://golang.org/dl/](https://golang.org/dl/)
* Open a terminal window
* Execute the following commands
  1. `mkdir ~/go`
  2. `export GOPATH=$HOME/go`
  3. `export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`
  4. `go version`

It should display the go version, ex. `goX.X.X darwin/amd64`

### Create Wallet

Note: Git is required for the remaining setup steps.

* Open a terminal
* Execute the following commands to download wallet CLI
  * `mkdir $HOME/nimble && cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/wallet-public.git`
  * `cd wallet-public`
  * `make install`
* Locate this path and confirm it exists (replace \<you> with your username)
  * `/Users/<you>/go/bin/nimble-networkd`
* Execute the following command to create your wallet. Give your wallet a name, such as 'ilovenimble'.
  * `[nimble-networkd path]/nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)`

The “address: nimblexxxx” output means your Nimble Network wallet address was created successfully!

### Start Mining

* Open a terminal window
  * `cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/nimble-miner-public.git`
  * `cd nimble-miner-public`
  * `make install`
  * `source ./nimenv_localminers/bin/activate`
  * `make run addr=<copy paste your “nimblexxx” wallet address here>`

To resume mining after your machine disconnects, re-run the command:

`make run addr=<copy paste your “nimblexxx” wallet address here>`

## Installing on Linux

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
* Locate this path and confirm it exists (replace \<you> with your username)
  * `/home/<you>/go/bin/nimble-networkd`
  * Copy this path value and use it in the next step.
* Execute the following command to create your wallet. Give your wallet a name, such as 'ilovenimble'.
  * `[nimble-networkd path]/nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)` The “address: nimblexxxx” output means your Nimble Network wallet address was created successfully!

### Start Mining

Note: python3.9 (or above) and pip3 are required for the remaining steps

* Open a terminal window
* Install python3 venv for Linux
  * `sudo apt update`
  * `sudo apt install python3-venv`

> If you encounter a failure while installing python3-venv, please execute the following commands.
>
> ```shell
> sudo apt-get install software-properties-common
> sudo add-apt-repository ppa:deadsnakes/ppa -y
> sudo apt install python3-venv
> ```

* Open a terminal window
  * `cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/nimble-miner-public.git`
  * `cd nimble-miner-public`
  * `make install`
  * `source ./nimenv_localminers/bin/activate`
  * `make run addr=<copy paste your “nimblexxx” wallet address here>`

To resume mining after your machine disconnects, re-run the command:

`make run addr=<copy paste your “nimblexxx” wallet address here>`

## Congrats 😘

You are now mining NIM!

For assistance, find us in our Discord server - [https://discord.gg/nimble](https://discord.gg/nimble)
