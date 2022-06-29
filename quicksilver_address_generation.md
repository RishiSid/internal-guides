# Generating address for Quicksilver Network
## 1. Using Keplr
### 1.1 Install the Keplr Wallet extension
Go to https://www.keplr.app/ and click on `Install Keplr for Chrome`

### 1.2 Create / import wallet
Once you've isntalled the extension, pin it on Chrome for easy access. Connect your Ledger or create a paper wallet (securely back up your seed phrase!)

- Click on the extension in the Chrome/Brave toolbar and the following page will open up
![account1](./screenshots/account1.png)
- In case you do not have an existing Keplr account you can create a new account

> **Note:** For paper wallets, you will be shown 12 words as your mnemonic seed. Select24 words option for a more secure mnemonic. Back it up securely (read the warning below). 

- Enter an account name and a passphrase to unlock your wallet. You will be asked for the mnemonic again. Enter the 24 words in order. This is to make sure you remember the mnemonic.

![account2]<img source="./screenshots/account2.png" width=100/>

> **Warning:** Make sure to securely back up your seed phrase. Whoever has your seed phrase has the control of your funds. If you loose your seed phrase, you loose access to the funds. There is no way to recover your seed phrase!

- Finally, click on Next to create your wallet
![account3](./screenshots/account3.png)

### 1.3 Add to Keplr
Visit http://vps.mkaczanowski.pro:8999/ to add Quicksilver as a network to Keplr. Choose Quicksilver network in Keplr. You will be shown the address there. Copy your address which starts with `quick...` and paste it in the following file against your name.

### 1.4 Paste your address in the allocation sheet
**Update your address in the list**

[Quicksilver Airdrop Allocation Sheet](https://docs.google.com/spreadsheets/d/1ggb_UiL8P3bqKv5C9H8dKGq7gPK3G-1JvqxwzPwtWoQ/edit#gid=0)

## 2. Using The Command Line
This guide will help you generate an address for the Quicksilver network using terminal (command line). It is a very easy guide to follow so anyone with access to Git and a terminal can do this.

## 2.1 Requirements
1. Git
2. Golang (installed on your system)

## 2.2 Build Quicksilver CLI tool
This step expects that the user already has Git and Golang installed. Mac users can use Homebrew to install these.

```
$ git clone https://github.com/ingenuity-build/quicksilver.git
$ cd quicksilver
$ git checkout tags/v0.3.0
$ make build
$ cd build
```
![clone](./screenshots/clone.png)
![checkout](./screenshots/checkout.png)

Upon listing the contents of the build directory you should see the `quicksilverd` executable. This is what we will use next to generate our address.

## 2.3 Generating address using Ledger
This step assumed you have a ledger device connected via USB to your machine. Make sure the Cosmos app is installed and open on Ledger before you perform this step. When you run the following command you will be asked to review the transaction on Ledger. Hit `Approve` once you have reviewed all the fields on Ledger.

```
$ ./quicksilverd keys add my-key-name --ledger 


- name: my-key-name
  type: ledger
  address: quick15q94h723t1v444q2po10iurfkgq659lnzdcp35
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"Wi1ZloQklTNwBPEbxj0GEnMivbdTiPo85jo+1qL34sxV"}'
  mnemonic: ""
```


![review](./screenshots/review_ledger.jpeg)
![approve](./screenshots/approve_ledger.jpeg)

## 2.4 Generating address using an old mnemonic
This step is for those users who do not possess a Ledger or want to generate a Quicksilver address from their raw mnemonic. 


> _The mnemonic shown below is a random one and doesn't correspond to any real address. It is just used for illustration purposes_

```
$ ./quicksilverd keys add my-key-name --interactive
> Enter your bip39 mnemonic, or hit enter to generate one.
ice dwarf wonder woman moriarty rubber ship cosmos rack hurt idea drop zintec mule strange ironman flash power thanos stick zoomcar nordic half fango
> Enter your bip39 passphrase. This is combined with the mnemonic to derive the seed. Most users should just hit enter to use the default, ""


- name: my-key-old-mnemomic
  type: local
  address: quick1dfgtqrxqeuf9po4prarewjlam2a9nrjty54xae
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"Dk22D0qtilaKQEmeTxrjXXowoy753v8HupMJtJmAcW52"}'
  mnemonic: ""


**Important** write this mnemonic phrase in a safe place.
It is the only way to recover your account if you ever forget your password.

ice dwarf wonder woman moriarty rubber ship cosmos rack hurt idea drop zintec mule strange ironman flash power thanos stick zoomcar nordic half fango
```

## 2.5 Generating address using a new mnemonic
This step is for those users who want to generate a paperwallet and a quicksilver address from scratch. In this step you will generate a 24-word mnemonic. 

> **Note:** You must BACK UP this mnemonic in a safe place. This is going to be your only way to access your funds. **If you loose this, you loose access to your funds!** Anyone in posession of this mnemonic can steal your funds!

```
$ ./quicksilverd keys add my-key-new-mnemomic

- name: my-key-new-mnemomic
  type: local
  address: quick1wel9cittgvpo23fumg5cchgmv8tlm9l2ginesh
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"Jpiter8s/z5nR/M63wAZ8ZaQ+Nhsahasgh/ADf3HEz0Z"}'
  mnemonic: ""


**Important** write this mnemonic phrase in a safe place.
It is the only way to recover your account if you ever forget your password.

word1 word2 word3 word4 soon allword some word could drink plastic target indoor material city need file zone lambo greece town never goat arrest
```

### 2.6 Update the excel sheet

**Update your address in the list**

[Quicksilver Airdrop Allocation Sheet](https://docs.google.com/spreadsheets/d/1ggb_UiL8P3bqKv5C9H8dKGq7gPK3G-1JvqxwzPwtWoQ/edit#gid=0)

---

## Recommendations

The safest option is to use the ledger, since your private key / mnemonic never “leaves” the device (you can’t extract it). In the CLI output you can see the field: `address: quick....` That is your wallet address!