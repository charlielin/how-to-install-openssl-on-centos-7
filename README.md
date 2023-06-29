# How To Install OpenSSL 1.1.1 on CentOS 7

This tutorial goes through how to install openssl 1.1.1 on CentOS 7, since the yum repo only installs up to openssl 1.0.

## Requirements

Upgrade the system

```
yum -y update
```

Install required packages

```
yum install -y make gcc perl-core pcre-devel wget zlib-devel
```

Download the latest version of OpenSSL source code

```
wget https://ftp.openssl.org/source/openssl-1.1.1k.tar.gz
```

## Configure, build and install OpenSSL

Uncompress the source file

```
tar -xzvf openssl-1.1.1k.tar.gz
```

Change to the OpenSSL directory

```
cd openssl-1.1.1k
```

Configure the package for compilation

```
./config --prefix=/usr --openssldir=/etc/ssl --libdir=lib no-shared zlib-dynamic
```

Compile package

```
make
```

Test compiled package

```
make test
```

Install compiled package

```
make install
```

## Export library path

Create environment variable file

```
vim /etc/profile.d/openssl.sh
```

Add the following content

```
export LD_LIBRARY_PATH=/usr/local/lib:/usr/local/lib64
```

Load the environment variable

```
source /etc/profile.d/openssl.sh
```

## Verify the OpenSSL version

```
openssl version
```
