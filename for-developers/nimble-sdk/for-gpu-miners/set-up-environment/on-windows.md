# On Windows

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
  * `make run test addr=<copy paste your “nimblexxx” wallet address here>`
