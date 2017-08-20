Phusion Passenger® 4.0 web server and application server
========================================================

This container image includes Phusion Passenger® 4.0 web server and application server for OpenShift and general usage.
Users can choose between RHEL and CentOS based images.
The RHEL image is available in the [Red Hat Container Catalog](https://access.redhat.com/containers/#/registry.access.redhat.com/rhscl/passenger-40-rhel7)
as registry.access.redhat.com/rhscl/passenger-40-rhel7.
The CentOS image is then available on [Docker Hub](https://hub.docker.com/r/centos/passenger-40-centos7/)
as centos/passenger-40-centos7.


Description
-----------

Phusion Passenger 4.0 web server and application server configured 
with Apache httpd web server. It also provides a Ruby 2.2 platform for 
building and running applications. Node.js 0.10 is preinstalled for 
assets compilation.

The image can be used as a base image for other applications based on Phusion Passenger® 4.0 or using s2i tool.


Usage
-----

To build a simple [puma-sample-app](https://github.com/sclorg/passenger-container/tree/master/4.0/test/puma-test-app) application
using standalone [S2I](https://github.com/openshift/source-to-image) and then run the
resulting image with [Docker](http://docker.io) execute:

*  **For RHEL based image**
    ```
    $ s2i build https://github.com/sclorg/passenger-container.git --context-dir=4.0/test/puma-test-app/ rhscl/passenger-40-rhel7 sample-server
    $ docker run -p 8080:8080 sample-server
    ```

*  **For CentOS based image**
    ```
    $ s2i build https://github.com/sclorg/passenger-container.git --context-dir=4.0/test/puma-test-app/ centos/passenger-40-centos7 sample-server
    $ docker run -p 8080:8080 sample-server
    ```

**Accessing the application:**
```
$ curl 127.0.0.1:8080
```


Configuration
-------------
No further configuration is required.


S2I build support
-------------
This Docker image supports the S2I tool (see Usage section). 
This image contains and enables the `rh-ruby22`, `rh-ror41`, `nodejs010`, `rh-passenger40`, and `httpd24` Software Collections. 
It is especially designed to support automatic S2I builds.

Environment variables and volumes
-------------
No special environment variables or volumes available.

Troubleshooting
---------------
Passenger logs into standard output, so the log is available in the container log. The log can be examined by running:

    docker logs <container>


See also
--------
Dockerfile and other sources for this container image are available on
https://github.com/sclorg/passenger-container.
In that repository, Dockerfile for CentOS is called Dockerfile, Dockerfile
for RHEL is called Dockerfile.rhel7.
