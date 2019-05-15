Simple Dockerized Barbican
===========================

Warning: This is a personal docker image that is designed to aid
in the development and testing of Barbican.

**Here be Dragons! Use at your own risk!!**

Starting a container
----------------------

```
sudo docker run \
    -d
    -p 9311:9311 \
    -v $LOCAL_BARBICAN_CONFIGS:/etc/barbican \
    --network host \
    --name barbican \
    -t barbican:v1
```

Because we start barbican container with host network mode, for
accessing keystone in the right way, we also need to update the
/etc/hosts file. We need to add a record like

```
192.168.2.177     keystone
```

the ip/host is which we can access keystone using it.

About the image
-------------
Exposed Ports:

 * ```9311``` - Public API Endpoint
 * ```9312``` - Admin API Endpoint

This image is expecting a volume containing all required
configuration files for Barbican or a link to a Keystone
container.
