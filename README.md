# bind9
[![Docker Pulls](https://img.shields.io/docker/pulls/abilioesteves/bind9.svg)](https://hub.docker.com/r/abilioesteves/bind9)

A simple Bind9 server image with a test.com zone for testing purposes

# Try it yourself
Simply run the provided `docker-compose.yml` file with `docker-compose up` or even with `docker stack deploy`.

After it's up and running, check if it works by using the `nslookup` utility:

```
nslookup ns1.test.com <host ip>
```

It should give you:

```
Name:	ns1.test.com
Address: 0.0.0.0
```

Where `<host ip>` is the IP address of the Docker Host that is running the BInd9 instance. If you're running it local, replace it with localhost:

```
$ nslookup ns1.test.com localhost

Server:		localhost
Address:	127.0.0.1#53

Name:	ns1.test.com
Address: 0.0.0.0

```

# Keys

A pair of TSIG keys is provided to securely manage the `test.com` zone:

1. Ktest.com.+157+50086.key
2. Ktest.com.+157+50086.private

To securely manage the zone with `nsupdate` requests, just map the `/keys` folder to a volume so it can be shared with other services.
