# bash-otp
One-Time Password generator for CLI using bash, oathtool.

Automatically copys the token into your computer's copy buffer (MacOS only atm)

This is basically "Authy for the CLI"

This script supports both encrypted and plain-text token files, but my reccomendation is to use encryption.

### Requirements

* oathtool (http://www.nongnu.org/oath-toolkit/)
* OpenSSL
* xclip (Linux)

### macOS Setup

```bash
brew install oath-toolkit gawk
```

## Description

Set of bash shell scripts to generate OTP *value* from token using TOTP.

### Usage

First ensure that there is a directory "tokenfiles" in the main dir where the script resides.

1. Create token file and encrypt it. Resulting file, "tokenfiles/tokenname.enc", is an encrypted file containing the token
  1. Put your token in a plaintext file in the tokenfiles/ directory:
  ```bash
  $ echo "1234567890abcdef" > tokenfiles/tokenname
  ```
  
  1. Encrypt the file with the included shell script:
  ```bash
  $ ./otp-lockfile tokenfiles/tokenname
  Password: (enter a good password)
  ```
  
  1. Confirm it worked:
  ```bash
  $ ls tokenfiles/
  tokenname.enc
  ```

1. Run otp; will produce roughly the following output:
  ```
$ ./otp tokenname
Password:
02: 123456
  ```

The number on the left is the seconds counter; a new TOTP token is generated every 30 seconds.

The number on the right is the 6-digit One-Time Password.

This will be copied directly into the paste buffer. Just press "Command-V" (or "CTRL-V" on Linux) to paste into a login dialog.


## Contents

* Script to do the actual value generation
* Script to encrypt the token in a file
* Script to decrypt same
* Empty "tokenfiles/" directory

