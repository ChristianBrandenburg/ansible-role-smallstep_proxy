# ansible-role-smallstep_proxy

This Ansible role is used to setup Nginx proxy for a specific port with an SSL/TLS certificate provided by a Smallstep CA.

If you for example have an application running on port 8989 and wish to serve it on port 443 with SSL/TLS.
This role will install git and then download Smallstep CLI, configure it with your Smallstep CA, and order a SSL/TLS certificate for your server hostname.
It will then install Nginx, set up a proxy_pass for your port (in this case 8989) to port 443 and configure HTTPS with the Smallstep certificate.

## Requirements
- Smallstep CA
- Ansible

## Usage

Provide your own values in [vars/main.yml](vars/main.yml)

`domain`
This is the root domain used in your environment. Smallstep will issue a certificate to hostname.yourdomain.com

`url`
This is the URL for your Smallstep CA fx. https://smallstep.yourdomain.com

`fingerprint`
This is the fingerprint of your Smallstep CA. When you start your Smallstep CA with `step-ca` command the fingerprint will be printed in the console.

`smallstepversion`
This is the version of Smallstep CLI you wish to install fx. 0.24.4

`proxyport`
This is the port that you wish proxy_pass in Nginx.

## Warning

The role does not set up firewall rules to block the original application port
