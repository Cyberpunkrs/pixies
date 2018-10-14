**"men in their prime, if they have convictions, are tasked to act on them."**

## howto

so, lets begin;

in this tutorial i am going to make a simple demo of the setup of a web service using a hidden service a.k.a. .onion domain, bad darkweb site that sells people and so on and for that i will use a debian container with docker


first lets make sure we have docker installed

`curl -fsSl https://get.docker.com/ | sh`

or you can install with your packager manager(apt, pacman, yum, etc) if available

then check if docker is ok:

`docker --version`

if everything is ok, lets begin the real thing

`docker run -ti /bin/bash`

then run `apt update && apt upgrade`

to make this a kiss howto im not going to compile from source what i might install but you are free to do it

`apt install apache2 tor nano`

`service apache2 start`

and lets configure tor hidden service

`nano /etc/tor/torrc`

and add the following lines:(you can change the dir, port for your will)

```
HiddenServiceDir /var/lib/tor/howto_hiddenservice/
HiddenServicePort 80 127.0.0.1:80
```

this conf works like: tor run the .onion domain on port 80 and listen locally on 127.0.0.1(localhost) at port 80, which in this case is apache. In other words we are telling tor to work as a webserver


then lets start tor and see the random generated onion domain for us

`service tor start`

`cat /var/lib/tor/howto_hiddenservice/hostname`
`biv3tp7csuwnlwsu.onion`

in some other machine or your host machine lets see if domain is working

`torsocks http biv3tp7csuwnlwsu.onion`
or
`torsocks curl -I biv3tp7csuwnlwsu.onion`
or
use tor browser

well, if everything is ok, it should work

to quit docker use: **ctrl + p + q**
to make sure the container is still running: `docker ps`

as long as the container is running(docker deamon is up) the hidden service should stay online

**now what?**
well, having access to tor opens a lot of doors. you can make a mirror of https://wikileaks.org or https://eff.org or https://wikipedia.org or create the next silk road(why not?)

**!!READ THIS PLEASE!!**
hosting a hidden service can be very dope but do not fucking forget to make sure it is secure, that it does not leak you fucking ip or that any kid can do some shit with your thing. so start by reading: https://blog.0day.rocks/securing-a-web-hidden-service-89d935ba1c1d


**remember, they are policing us**

also, as i said before, having the anonymity that tor and any cryptology technology provide is a gift and because of that we have to let everyone know about it.
tell your uncle, your dog, your mom, grandpa and your teachers about tor and how they should protect their data and maintain their privacy secure.


#### signed by cyberpunkrs
https://t.me/cyberpunkrs
