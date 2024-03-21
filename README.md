---
description: A short guide to mining on Nimble
---

# Mining on Nimble

## Community Setup Guide

Use these instructions to configure your mining hardware and mine NIM.

Instructions are available for Linux, Windows 11, and Mac.

## Prerequisites

#### Windows 11

* Install Windows Subsystem for Linux (WSL)
  * [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)
* Once completed, follow the Linux instructions below

### Mac Go Setup

* Download and install Golang
  * [https://golang.org/dl/](https://golang.org/dl/)
* Open a terminal window
* Execute the following commands
  1. `mkdir ~/go`
  2. `export GOPATH=$HOME/go`
  3. `export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`
  4. `go version`

It should display the go version, ex. `goX.X.X darwin/amd64`

### Linux/Windows Go Setup

* Open a terminal
* Execute the following commands
  * `sudo apt update`
  * `sudo apt install golang`
  * `export GOPATH=$HOME/go`
  * `export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`
  * `go version`

It should display the go version.

### Install Nimble’s Wallet CLI

Note: Git is required for the remaining setup steps.

* Open a terminal
* Execute the following commands
  * `mkdir $HOME/nimble && cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/wallet-public.git`
  * `cd wallet-public`
  * `make install`

### Get the nimble-networkd path

**Macbook**

* Locate this path and confirm it exists
  * `/Users/<you>/go/bin/nimble-networkd`

**Linux/Windows**

* Locate this path and confirm it exists&#x20;
  * `/home/ubuntu/go/bin/nimble-networkd`

Copy this path value and use it in the next step.

### Create your Wallet

To begin, come up with a name for your wallet. We suggest "ilovenimble".

* Execute the following command
  * `[nimble-networkd path]/nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)`

The “address: nimblexxxx” output means your Nimble Network wallet address was created successfully!

## Start mining

### Prepare Python Environment (Linux/Windows Only)

Note: python3.9 (or above) and pip3 are required for the remaining steps

* Open a terminal window
* Install venv for Linux
  * `sudo apt update`
  * `sudo apt install python3-venv`

This step is not required for Mac.

### Start Mining&#x20;

* Open a terminal window
  * `cd  $HOME/nimble`
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

\


\
