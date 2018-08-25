# cloudtools
make working with or in the cloud easier

## Install All
```bash
git clone https://github.com/cleanmedia/cloudtools.git
```

## source spi: Set PIN - without traces

### Example

Put a Password (PIN) into the bash environment - without leaving traces:
```bash
source spi
```

* It will ask for a new PIN, if the bash variable $PIN is empty.
* Otherwise it will confirm, that the PIN was already set priviously.


## fcr: File Crypt - Script to compress-encrypt/check/decompress-decrypt a File

### Example

* Compress a file containing secrets
* encrypt it using the secret from the PIN environment variable
* and delete the plain text version
* store the file as filename.enc.7z

```bash
fcr e filename
```

* Decompress/Decrypt filename.enc.7z
* using the PIN variable (or ask for it)
* keep the plain text filename
* delete filename.enc.7z

```bash
fcr d filename.enc.7z
```


## abu: AWS Backup - Local Directory to S3

### Prerequisites

* AWS User and access to its S3 service.
* some kind of Linux and the AWS CLI package
* define ~/.aws/config defaults
* A bucket for those backups only:
* aws s3 mb s3://${my-global-backup-bucket-name}
* Edit your global bucket name vaiable 'BUCK' in the file abu.
* Have a PIN ready in your mind, that you don't forget but is safe and unique.
* As for example Ablibtnlaci10t!
* Meaning the initials of the sentence:
* A bad life is better than no life and can improve 10 times!
* You can use the command "source spi" to set the PIN only once and reuse it many times.

### Examples

Show the contents of my backup bucket:
```bash
abu s
```

Compress and encrypt the current local directory, name it dirname and send it to the S3 bucket.
```bash
abu b dirname
```

Restore the object dirname.7z from the S3 bucket to the local directory and decrypt it.
```bash
abu r dirname
```

Delete th S3 object dirname.7z from the backup bucket.
```bash
abu d dirname
```

Compress the local directory only and encrypt it and store it as dirname.7z.
```bash
abu c dirname
```


