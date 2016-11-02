# Description

Simple script to manage certificates. Currently only supports certificates obtained from **quay.io/letsencrypt/letsencrypt** or any other Lets Encrypt image that stores the certificates in the same place and manner.

## Usage

Since this image is designed to facilitate communication between different containers (webserver, etc and certificate obtainer), it is highly recommended to use volumes to help facilitate this. Certificates are managed by passing three arguments to the script: **domain**, **source type**, and **destination type**. Currently, the only supported source type is **letsencrypt** and the only supported destination type is **hiawatha**.

## Examples

Given a **quay.io/letsencrypt/letsencrypt** container that has a volume defined **-v letsencrypt:/etc/letsencrypt** and a website using **taosnet/hiawatha** with a volume defined **-v hiawatha_certs:/certs**.
```
docker run --name mysite.com-ssl-broker -v letsencrypt:/etc/letsencrypt -v hiawatha_certs:/certs taosnet/cert-manager mysite.com letsencrypt hiawatha
```
