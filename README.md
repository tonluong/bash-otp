# bash-otp

Command line 2FA. 2-Factor verification similar to Google Authenticator and Authy.

* TOTP (Time-based One-Time Password) using oathtool
* Encrypt / Decrypt using OpenSSL
* Copies to clipboard using `pbcopy` (macOS); `xclip` (Linux)
* Supports both encrypted and plain-text token files


### Requirements

* oathtool (http://www.nongnu.org/oath-toolkit/)
* OpenSSL
* xclip (Linux)


## Setup
### macOS

```bash
brew install oath-toolkit gawk
```

### Linux
```bash
$ sudo aptitude install -y oathtool libpam-oath
$ sudo aptitude install -y xclip
```


## Contents

* **otp** - Read tokenfile and generate TOTP value
* **otp-lockfile** - Encrypt tokenfile, remove original file and save new encrypted tokenfile in **tokenfiles/** folder
* **otp-unlockfile** - Decrypt tokenfile and save to plain-text file
* **/tokenfiles/** - Empty folder




## Usage

**otp**

```bash
$ ./otp amazon		# reads tokenfiles/amazon[.enc]
Password:
29: 123456
59: 008256
10: 193842 
```

Paste value from clipboard 

* <kbd>&#x2318; Command</kbd> + <kbd>v</kbd> 
* <kbd>Ctrl</kbd> + <kbd>v</kbd>

**otp-lockfile**

```bash
$ echo "1234 1234 1234" > tokenfiles/amazon

$ ./otp-lockfile tokenfiles/amazon
Password:
Verify Password: 

$ ls -l tokenfiles/

```




