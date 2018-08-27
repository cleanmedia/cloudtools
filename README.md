# cloudtools
make working with or in the cloud easier and more confidential

## Install All
```bash
git clone https://github.com/cleanmedia/cloudtools.git
mkdir -p /usr/local/bin
cd cloudtools; sudo cp abu setpin filecrypt /usr/local/bin/
```

## source setpin
Set PIN - without traces

### Example

Put a Password (PIN) into the bash environment - without leaving traces:
```bash
source setpin
```

* It will ask for the new PIN to be put into the environment.


## filecrypt
File Crypt - Script to compress-encrypt/check/decompress-decrypt a File

### Example

* Compress a file containing secrets
* encrypt it using the secret from the PIN environment variable
* and delete the plain text version
* store the file as filename.enc.7z

```bash
filecrypt e filename
```

* Decompress/Decrypt filename.enc.7z
* using the PIN variable (or ask for it)
* keep the plain text filename
* delete filename.enc.7z

```bash
filecrypt d filename.enc.7z
```


## abu
AWS Backup - Local Directory to S3

### Prerequisites

* Igor Pavlov's 7z command line utility:
* apt-get install p7zip-full # for ubuntu
* AWS User and access to its S3 service.
* some kind of Linux and the AWS CLI package
* define ~/.aws/config defaults
* A bucket for those backups only:
* aws s3 mb s3://${my-global-folder-backup-bucket-name}
* Edit your global bucket name vaiable 'BUCK' in the file abu.
* Have a PIN ready in your mind, that you don't forget but is safe and unique.
* As for example Ablibtnlaci10t!
* Meaning the initials of the sentence:
* A bad life is better than no life and can improve 10 times!
* You can use the command "source setpin" to set the PIN only once and reuse it many times.

### Examples

Show the objects (content) of my backup bucket:
```bash
abu s
```

Compress and encrypt the current local directory, and send it as objname.7z to the S3 bucket.
```bash
abu b objname
```

Restore the object objname.7z from the S3 bucket to the local directory and decrypt/unpack it.
```bash
abu r objname
```

Delete th S3 object objname.7z from the backup bucket.
```bash
abu d objname
```

Compress the local directory only and encrypt it and store it as objname.7z.
```bash
abu c objname
```


