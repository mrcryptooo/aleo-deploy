discord handle: mrcryptoo
<img alt="Aleo" width="1412" src="https://biaupload.com/do.php?imgf=org-1a286c7c34641.jpg">

## Aleo-deploy-for-mrcryptoo

First prepare the prerequisites and enter the following codes after starting. 

So let's go! step by step

I am using `Bitvise SSH Client` software to run the commands.

**When you connected by SSH to your server I copy and paste the commands line by line to prepare prerequisites on our server, so let's do it.**|

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
next 
```bash
source $HOME/.cargo/env
```

next
```bash
rustup install stable
```

next
```bash
rustup update stable
```

next
```bash
rustup default stable
```

next
```bash
git clone https://github.com/AleoHQ/leo
cd leo
```

next
```bash
apt install clang gcc libssl-dev pkg-config
```

next
```bash
cargo install --path .
```

next
```bash
git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS
```

next
```bash
./build_ubuntu.sh
```

And last one for this part
```bash
cargo install --path .
```
**At this point, you must have received Faucet via Twitter or SMS.**

so befor to get faucet you should [visit this site](https://faucetgreenlist.snarkos.net) to put your wallet address in green list.

When you done this step we can get our faucet by SMS, to do that we can throw a text message to
**`number : +1867-888-5688`**

```bash
Send 10 credits to aleo... (Your wallet address)
```

to get faucet by Twitter twite below line :
```bash
@AleoFaucet send 10 credits to aleo... (Your wallet address)
```

So excited till now 😍 when you received the faucet on your wallet try to run the final commands line by line. let's do it.

First command
```bash
cd $HOME
```

next
```bash
mkdir demo_deploy_Leo_app && cd demo_deploy_Leo_app
```

next, , be aware to put your wallet address in below
```bash
WALLETADDRESS="put-your-wallet-address-here"
```

next, be aware to put your wallet address in below
```bash
APPNAME=helloworld_"${WALLETADDRESS:4:6}"
```

next, here we create a new app
```bash
leo new "${APPNAME}"
```

next
```bash
PATHTOAPP=$(realpath -q $APPNAME)
```

next
```bash
cd $PATHTOAPP && cd ..
```

next, be aware to put your wallet private key in below
```bash
PRIVATEKEY="put-your-wallet-private-key-here"
```

Now go to [aleo.tools](https://aleo.tools) and use the value & view key of your faucet transation that you received.

<img alt="help to generate RECORD" width="1412" src="https://biaupload.com/do.php?imgf=org-5babe1c61bc91.png">

```bash
RECORD="put-the-code-that-you-get-it-here"
```

finally run below command

```bash
snarkos developer deploy "${APPNAME}.aleo" --private-key "${PRIVATEKEY}" --query "https://vm.aleo.org/api" --path "./${APPNAME}/build/" --broadcast "https://vm.aleo.org/api/testnet3/transaction/broadcast" --fee 600000 --record "${RECORD}"
```
