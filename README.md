# Encrypting Files on Linode Object Storage

This guide will take you through the process of creating a bucket and uploading/downloading encrypted files to and from it through a shell terminal.
### 1. Create Bucket
On the Linode dashboard, go to Object Storage and click "Create Bucket". Give it a label and select the desired region.
### 2. Create an Access Key
Go to the "Access Keys" tab next to the "Bucketss" tab and click on "Create Access Key". Give it a label and select "Create Access Key". Make sure to save the secret Access Key.


## Mac
### 1. Install command line tools
```
xcode-select --install
```

### 2. Install s3cmd and gpg
```
brew install s3cmd
brew install gpg
```



## Linux

### 1. Install pip and s3cmd
```
sudo apt update
sudo apt install python3-pip
sudo pip install s3cmd
```

## Continue Here:

### 4. Configure S3cmd
```
s3cmd --configure
```

#### Access Key: 
Paste your access key
  
#### Secret: 
Paste your secret access key
    
#### Default region: 
Press enter (don't type or add anything)
    
#### S3 Endpoint: 
Paste your cluster URL without 'https://'. 
Find a list of clusterURLs for each region
https://www.linode.com/docs/products/storage/object-storage/guides/urls/#cluster-url-s3-endpoint

#### DNS-style bucket+hostname:port template for accessing a bucket:
yourBucketName.S3Endpoint (The one from the last step)

#### Encryption Password:
Add a strong password to protect your files from reading by unauthorized persons while in transfer to S3

#### Path to GPG program:
Use default path

#### Leave everything else as default (Just press 'enter')

#### When the prompt appears to test access with the supplied credentials, enter n to skip. Currently, this process results in the following error - even when the settings are correct.
Please wait, attempting to list all buckets...
ERROR: Test failed: 403 (SignatureDoesNotMatch)

#### When the prompt appears to save your settings, enter Y. A configuration file named .s3cfg is created within your home directory.

### 6. Upload Encrypted Files:
```
s3cmd put file.txt s3://your-bucket/ -e
```

`-e` flag encrypts the file. RSA is default

### 7. Download Encrypted Files:
```
s3cmd get s3://your-bucket/file.txt -e

```
`-e` flag decrypts the file.




  




