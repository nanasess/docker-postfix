postfix-relayhost
==============

Run postfix with smtp relay.

## Requirement
+ Docker 1.0

## Installation
1. Build image

```bash
$ docker pull nanasess/postfix-relayhost
```

## Usage
1. Create postfix container with relayhost

Save your **relay_password** to /path/to/relay_password

```
[relayhost.example.com]:587	user@relayhost.example.com:password
```

Execute the `docker run` command.

```bash
$ docker run -p 1025:25 \
		-e maildomain=mail.example.com \
		-e relayhost="[relayhost.example.com]:587" \
		-v "/path/to/relay_password:/etc/postfix/relay_password" \
		--name postfix-relayhost -d nanasess/postfix-relayhost
```

## Note
+ Login credential should be set to (`username@mail.example.com`, `password`) in Smtp Client
+ You can assign the port of MTA on the host machine to one other than 25 ([postfix how-to](http://www.postfix.org/MULTI_INSTANCE_README.html))
+ Read the reference below to find out how to generate domain keys and add public key to the domain's DNS records

## Reference
+ [Postfix SASL Howto](http://www.postfix.org/SASL_README.html)
+ [How To Install and Configure DKIM with Postfix on Debian Wheezy](https://www.digitalocean.com/community/articles/how-to-install-and-configure-dkim-with-postfix-on-debian-wheezy)
+ https://github.com/catatnight/docker-postfix
+ TBD
