# TPM 2.0 alpine container

##

To build, go to the `alpine` directory, the one with the `Dockerfile`

```sh
docker build -t tpmcourse .
```sh

It will then build - if there are warnings then it probably doesn't matter. After it finishes, type:

```sh
docker images
```

You then should see something like

```sh
root@Debian:/home/ian/projects/TPMCourse/alpine# docker images
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
tpmcourse    latest    9975934a15d9   2 minutes ago   537MB
root@Debian:/home/ian/projects/TPMCourse/alpine#
```

To run, type:

```sh
docker run -it tpmcourse
```

If a prompt does not appear, then hit the enter key a few times - you should get a `#` prompt, meaning that you now have full root access to the container.

Try then running a TPM command, for example,  `tpm2_getrandom --hex 16`, you should then get output as shown below:

```sh
root@Debian:/home/ian/projects/TPMCourse/alpine# docker run -it tpmcourse
LIBRARY_COMPATIBILITY_CHECK is ON
Manufacturing NV state...
Size of OBJECT = 2600
Size of components in TPMT_SENSITIVE = 1096
    TPMI_ALG_PUBLIC                 2
    TPM2B_AUTH                      66
    TPM2B_DIGEST                    66
    TPMU_SENSITIVE_COMPOSITE        962
Starting ACT thread...
/ # TPM command server listening on port 2321
Platform server listening on port 2322
Command IPv6 client accepted
Platform IPv6 client accepted

/# tpm2_getrandom --hex 16
6822a3e685f5c448b455560d6628a969
```


## Other Stuff - ignore



NB: Refer to the README.md in the main directory for installation and usage instructions

The base image for the container is **alpine:latest**.

Dependecies for building the TCG TPM2 Software Stack are:

* autoconf
* autoconf-archive
* automake
* libtool
* build-base
* pkgconf
* doxygen
* json-c-dev
* openssl
* openssl-dev
* libssl1.1
* git
* udev 
* dbus
* curl-dev
* linux-headers
* glib-dev
* libconfig-dev
* libgcrypt-dev
* wget

It is possible to further strip down dependecies, some packages are only used for
building the documentation which is not in use inside the container as
default.

