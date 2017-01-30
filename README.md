# letsencrypt-nginx
Solution for quick creation and renewal of letsencrypt ssl certificates and vhost configuration.
Was developed and tested on Ubuntu 16.04 so unknown compability with other OSes

## What does it do?
This renew script is dual purpose, it creates vhosts with an initial ssl from letsencrypt and renews them.

## Installation
First of all, you need to have **nginx**, **letsencrypt**, **bc** installed for this to work.

Afterwards, just follow the folder structure in this repo and make sure those folders and files is placed in the proper structure in root (/).

Then in **/usr/local/bin/renew** add a reclaim email address before proceeding.

## Before use
Make sure the DNS records gets pointed towards the server which runs the nginx instance.

## Usage #1 (creation of vhosts)
```bash
$ renew test.example.com
```
if no nginx configuration is located in **/etc/nginx/sites-available** then you will be
prompted with a message asking you if you which to create this vhost.

After confirmation, step-1 will be copied and named the same name as the parameter.
Nginx gets reloaded, a configuration gets placed in /etc/letsencrypt with the same name as the parameter.
Letsencrypt gets called and certificates gets created.

When that is done, step-2 will be copied and overwrite the previous configuration and nginx gets reloaded once again, and now you should see that your domain has SSL in the browser.

## Usage #2 (creation of certificate)
```bash
$ renew test.example.com
```
if a nginx configuration is present, the renewal script will check if a letsencrypt configuration
is located in /etc/letsencrypt and if not, one will be created.
Afterwards the renewal script will check if a certificate is present, if not letsencrypt will be called for creation of the certificate.

## Usage #3 (renewal of certificate)
```bash
$ renew test.example.com
```
if a configuration and certificate is present, this script will check when the certificate will expire. and if it has not expired yet this
script will just present the days left until expiration. if the certificate is expired or one day from getting expired it will renew it.

## Thats it
Feel free to improve this solution, grammar, explanation. Fork it and create a pull request.
