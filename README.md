Phusion Passenger container images
===============================

This repository contains Dockerfiles for Phusion Passenger images for OpenShift.
Users can choose between RHEL, Fedora and CentOS based images.

For more information about contributing, see
[the Contribution Guidelines](https://github.com/sclorg/welcome/blob/master/contribution.md).
For more information about concepts used in these container images, see the
[Landing page](https://github.com/sclorg/welcome).


Versions
---------------
Passenger versions currently provided are:
* [passenger-4.0](4.0)

RHEL versions currently supported are:
* RHEL7

CentOS versions currently supported are:
* CentOS7


Installation
---------------
To build a Passenger image, choose either the CentOS or RHEL based image:
*  **RHEL based image**

    These images are available in the [Red Hat Container Catalog](https://access.redhat.com/containers/#/registry.access.redhat.com/rhscl/passenger-40-rhel7).
    To download it run:

    ```
    $ docker pull registry.access.redhat.com/rhscl/passenger-40-rhel7
    ```

    To build a RHEL based Passenger image, you need to run the build on a properly
    subscribed RHEL machine.

    ```
    $ git clone --recursive https://github.com/sclorg/passenger-container.git
    $ cd passenger-container
    $ git submodule update --init
    $ make build TARGET=rhel7 VERSIONS=4.0
    ```

*  **CentOS based image**

    This image is available on DockerHub. To download it run:

    ```
    $ docker pull centos/passenger-40-centos7
    ```

    To build a Passenger image from scratch run:

    ```
    $ git clone --recursive https://github.com/sclorg/passenger-container.git
    $ cd passenger-container
    $ git submodule update --init
    $ make build TARGET=centos7 VERSIONS=4.0
    ```

**Notice: By omitting the `VERSIONS` parameter, the build/test action will be performed
on all provided versions of Passenger.**


Usage
---------------------------------

For information about usage of Dockerfile for Passenger 4.0,
see [usage documentation](4.0/README.md).

Test
---------------------
This repository also provides a [S2I](https://github.com/openshift/source-to-image) test framework,
which launches tests to check functionality of a simple Passenger application built on top of the passenger image.

Users can choose between testing a Passenger test application based on a RHEL or CentOS image.

*  **RHEL based image**

    To test a RHEL7 based Passenger image, you need to run the test on a properly
    subscribed RHEL machine.

    ```
    $ cd passenger-container
    $ git submodule update --init
    $ make test TARGET=rhel7 VERSIONS=4.0
    ```

*  **CentOS based image**

    ```
    $ cd passenger-container
    $ git submodule update --init
    $ make test TARGET=centos7 VERSIONS=4.0
    ```

**Notice: By omitting the `VERSIONS` parameter, the build/test action will be performed
on all provided versions of Passenger.**
