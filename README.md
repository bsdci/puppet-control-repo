# A Puppet Control Repository

This Code is based on [Puppet Inc's Control-Repo](https://github.com/puppetlabs/control-repo).

We use it to test the "remote" feature in [ioc's Puppet Provisioning Plugin](https://github.com/bsdci/libioc/pull/629)

## How to use

To use this repo yourself, create a jail with the following settings:

```sh-session
root@host # ioc create webserver \
  provision.method=puppet \
  provision.source=https://github.com/bsdci/puppet-control-repo
webserver successfully created from 12.0-RELEASE!
```

Then provision the jail with:

```sh-session
root@host # ioc provision webserver
```

## What it does

This should install nginx and serve a hello-world html, you can test it with:


```sh-session
root@host # curl http://<webserer-ip>
<html>
  <head>
    <title>Hello, World</title>
  </head>
  <body>
    <h1>Hello, World</h1>
    <p>Hello, World</p>
  </body>
</html>
```
