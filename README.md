# Ghost installation from chef and vagrant

This is a simple example for chef usage in a single server. We install ghost framework as an example.

## Installation

It should work out of the box. It requires virtualbox and vagrant. Once you have it...

```
git clone git@github.com:alinefr/vagrant-ghost.git
cd vagrant-ghost
vagrant up local
```

We need to find out what is your IP address. Login in your machine:

```
vagrant ssh local
```

Once there type the following:
```
sudo ip addr show
```

Of course your output may be a little different than mine. But not too different.

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 02:1f:97:0f:e2:73 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::1f:97ff:fe0f:e273/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:63:bf:db brd ff:ff:ff:ff:ff:ff
    inet 172.28.128.3/24 brd 172.28.128.255 scope global enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe63:bfdb/64 scope link
       valid_lft forever preferred_lft forever
```

So we have three network interfaces. lo (our loopback), enp0s3 (the vagrant interface) and enp0s8 (the interface to our host which works without vagrant help).

enp0s8 is 172.28.128.3 as you can see from the output above. 

Get to http://172.28.128.3. On your first attempt you may get 'bad gateway'. Wait at least 5 minutes, because it's the time it needs to be built and installed.
