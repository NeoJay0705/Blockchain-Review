
# Trezor Safe 3

A hardware wallet, called the device below, tries to protect your private key.

> Learn more information from [Official](https://trezor.io/learn)

# To Secure Wallet

Establishing protection from zero protection.

## (UNSECURED) Plaintext Private Key

You store/use the private key directly on the device.
> [Problem 1](#solving-problem-1-generating-the-private-keys-from-recovery-seeds): It has lots of private keys if you need many wallets.\
> [Problem 2](#solving-problem-2-storing-the-private-keys-on-the-device-using-encryption): The person who stolen your device can directly access your accounts.

## Solving Problem 1: Generating the Private Keys from ***Recovery Seeds***

> *Aim: Generating private keys from ***[Recovery Seeds](https://trezor.io/learn/a/how-to-use-a-recovery-seed)****

The *Recovery Seeds* will be finally transformed into many private keys.

> For the *Recovery Seeds* are hard to memorize, you must write down those seeds on paper.

### (Optional) **Advanced *Recovery Seeds*: [Shamir backup](https://trezor.io/learn/a/what-is-shamir-backup)**

> *RISK: You will lose your account when you lose your *Recovery Seeds* paper if using a single *Recovery Seeds*.*

One of the solutions is to split the seeds into many different papers and set a `threshold` to define how many seed papers to recover your account.

## Solving Problem 2: Storing the Private Keys on the Device using Encryption

> *Aim: Encrypting private keys using secrets that humans memorize*
>> *There is only one occasion when your Trezor will reveal your recovery seed, and that is during the backup procedure. Keep in mind that your Trezor will only show your recovery seed once.*

Solution: ***[PIN](https://trezor.io/learn/a/pin-protection-on-trezor-devices)***\
Encrypting/Decrypting *Recovery Seeds* by

1. *secret* from ***[Secure Element](https://github.com/Infineon/optiga-trust-m)***
2. *PIN* memorized by the human

>> *Your *PIN* is independent from the recovery seed phrase. This means you can set a new PIN using the Trezor recovery process in case you forget it.*

Solution: ***[Passphrase](https://trezor.io/learn/a/passphrases-and-hidden-wallets)***\
Encrypting/Decrypting private key by

1. *Recovery Seeds*
2. *Passphrase* memorized by the human

> where *Passphrase* is ~50 ASCII characters

> [Problem 3](#solving-problem-3-wallet-migration): Those solutions mitigate the losses but not eliminate the risk. The solutions give you the time to transfer your lost old wallets to new wallets before the hacker find out your private keys by brute force.

## Software Security

1. Download the application from Trezor's official website.
2. On the same page, Download the *Signature* and *Signing Key*
3. Install `gpg` based on your operating system
4. Check the file integrity

    ```sh
    gpg --import satoshilabs-2021-signing-key.asc

    gpg --verify Trezor-Suite-23.12.3-mac-arm64.dmg.asc Trezor-Suite-23.12.3-mac-arm64.dmg
    ```

## Firmware Security

>> 1. *All Trezor devices are distributed without firmware installed - you will need to install it during setup.* OR FAILED
>>
>> 2. *The bootloader verifies the firmware signature each time you connect your Trezor to a computer. Trezor Suite will only accept the device if the installed firmware is correctly signed by SatoshiLabs.*

# Solving Problem 3: Wallet Migration

> *Aim: To transfer the stolen wallets to new wallets as soon as possible, buying more than one device can immediately transfer after the *Recovery Seeds* is not safe.*

[Wallet Migration - trezor.io](https://trezor.io/learn/a/move-crypto-to-a-wallet-with-a-new-seed)
