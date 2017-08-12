
# certbot Fast-Guide (draft v0.1c)

`certbot` is a command-line software used in web-servers, and is part of EFF’s effort to encrypt the entire Internet. Check version with `certbot --version` and basic usage with `certbot --help`. Certbot can obtain and install [HTTPS](https://en.wikipedia.org/wiki/HTTPS)/[TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security) certificates.

This Guide is for both, beginners and experient users that need a cheatsheet. For any detail see the **complete `certbot` documentation** at https://certbot.eff.org/docs/ 

NOTES

This guide was elaborated with aims in the most frequently used commands of `certbot`, where "frequently" is not a statistical result, but a perception of active community.
It is also a  compilation of the *most common [Use Cases](https://en.wikipedia.org/wiki/Use_case)* of the `certbot`  software. When a *user decision* is necessary, the Guide use [convention-over-configuration](https://en.wikipedia.org/wiki/Convention_over_configuration) principle to avoid multiple recommendations, and it is explained as "tip".

The guide is organized into *scenarios* of use cases, supplying command or sequence of commands to each use case.  To help edit here, to discuss, see [certbot/issues/4961](https://github.com/certbot/certbot/issues/4961).

-----
(ToC here)

-----

## Install certbot

To install the `certbot` command, that is the *certbot* software, use the online form *"I'm using..."* at https://certbot.eff.org   <br/>Avoid any other site for this instructions, they are updated every time.

<!-- ## ## ## -->
## Scenario-1

Suppose that you have four domains to be certifyed, and the "most important domain" also the name of the certificate, 

* **Certificate Name**: `xxxx.org`
* **Domain** list (of one or more): `xxxx.org aaaaa.com aaaaa.org bbbbb.com`

### Create a certificate with one domain

One command: `certbot --cert-name xxxx.org -d xxxx.org`

Tip: use choose "Secure" when selecting HTTPS redirection strategy.

### Create a certificate with many domains

One command: `certbot --cert-name xxxx.org -d xxxx.org -d aaaaa.com -d aaaaa.org`. 

Option? `certbot --cert-name xxxx.org -d xxxx.org,aaaaa.com,aaaaa.org`. 

Tip: you can omit the `--cert-name xxxx.org` part, them the first `-d` option (`xxxx.org`) will be the *Certificate Name*. 

### Create a certificate with "unknown domains" in a "unknown server"

One command: `certbot`. 

Tip: it is interactive ... but ... ? reliable? Confusion NGINX vs Apache vs Manual? 

### Create a certificate with "unknown domains" in a NGINX server

One command: `certbot --nginx`. 

Tip: it is an interactive command-line interface (CLI),  answer with  caution each question.


### To test of simulate a certificate creation instruction

One command: add `--dry-run` option to your command. 

### Case ...
.... Please help adding more cases! ...

<!-- ## ## ## -->
## Scenario-2
After completed the certification in the *Scenario-1*, you need some usual maintenance tasks after basic installation.

### List a created certificate

One command: `certbot certificates`. 

Tip-1: check if all listed certificates are in use.

Tip-2: to list only domains of a specific *cert-name* as `MyCertName` use `certbot certificates --cert-name MyCertName`.

### Refresh (renew) the certificate once

One command: `certbot renew`

Tip: there are also an *automatic renew* procedure, see case "Refresh the certificate forever".

### Delete domains from a certificate
Is like to redo "Create a certificate" task... So, do it by subtracting from the domain list, the domain that you whant to delete. Example: supposing as in *Scenario-1* that you have a certificate   `xxxx.org` with domains {`xxxx.org`, `aaaaa.com`, `aaaaa.org`}, and suppose that you whant to delete `aaaaa.com`.

One command: `certbot --cert-name xxxx.org -d xxxx.org -d aaaaa.org`. 

Tip: check the certificate listing it.

### Delete a full certificate

If you see a created certificate by its *cert-name*, when list it, and not using it... Or other motivation to "purge all files" of this (eg. `MyCertName`) certificate. 

One command: `certbot delete --cert-name MyCertName`

### Cancel (revoke) a full certificate with transferred or compromised key 
If the certificate of, suppose, *cert-name* `MyCertName`, was transferred to another owner or its key was compromised, you need not only to "Delete a full certificate", but also to *revoke* it from internet. 

Commands, step-by-step: 

1. to check path from *cert-name*: `certbot certificates --cert-name MyCertName`
2. to revoke this *cert-name*: `certbot revoke --cert-path /etc/letsencrypt/live/MyCertName/fullchain.pem`
3. to purge all files: `certbot delete --cert-name MyCertName`
