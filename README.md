# A Puppet Control Repository

This Code is based on [Puppet Inc's Control-Repo](https://github.com/puppetlabs/control-repo).

We use it to test the "remote" feature in [ioc's Puppet Provisioning Plugin](https://github.com/bsdci/libioc/pull/629)

## How to use

To use this repo yourself, create a jail with the following settings:

```sh-session
root@host # ioc create web01 \
  provision.method=puppet \
  provision.source=https://github.com/bsdci/puppet-control-repo
web01 successfully created from 12.0-RELEASE!
```

Then provision the jail with:

```sh-session
root@host # ioc provision web01
```

## What it does

This should install nginx and serve a hello-world html, you can test it with:


```sh-session
root@host # curl http://<web01-ip>
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

## Custom Facts

You might be wondering if there's a standard method for setting facts.
For this we can use the `user.*` config namespace.
Along with a [custom fact](site/profile/lib/facter/ioc.rb) we can extract these names and values, as they are passed into the environment whenever a hook is run.

```sh-session
ioc set user.facts.role=webserver web01
ioc provision
```

We hope you find our custom facts script inspiring or useful!
