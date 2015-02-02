s3fs-fuse
=========

CentOS/RH/Amazon RPMs for S3FS-Fuse <https://github.com/s3fs-fuse/s3fs-fuse>

Based off the [spec file](http://kad.fedorapeople.org/packages/s3fs/s3fs.spec) created by [Jorge A Gallegos](http://kad.fedorapeople.org/), referenced at <https://bugzilla.redhat.com/show_bug.cgi?id=725292>, and upgraded by [Corey Gilmore](https://github.com/cfg), refered at <https://github.com/cfg/s3fs>

Includes RPMs for fuse-2.8.5 if needed.

Tested on x64 CentOS 5.11, 6.4 and Amazon Linux 2014.03


Requirements
------------

* Kernel-devel packages (or kernel source) installed that is the SAME version of your running kernel
* LibXML2-devel packages
* CURL-devel packages (or compile curl from sources at: curl.haxx.se/ use 7.15.X)
* GCC, GCC-C++
* pkgconfig
* FUSE (>= 2.8.4)
* FUSE Kernel module installed and running (RHEL 4.x/CentOS 4.x users - read below)
* OpenSSL-devel (0.9.8)
* Git
* rpmbuild


Building fresh RPMs
-------------------

Clone the repo: 

    git@github.com:juliogonzalez/s3fs-rpm.git
    cd s3fs-rpm


Build fuse-2.8.5 RPMs
---------------------

If you do not have fuse >= 2.8.4 available, then you may compile 2.8.5 using [fuse-2.8.5-99.vitki.01.el5.src.rpm](https://rpm.vitki.net/pub/centos/6/source/fuse-2.8.5-99.vitki.01.el5.src.rpm) from [rpm.vitki.net](https://rpm.vitki.net/pub/centos/6/source/)

Otherwise, you do not need this step, but install fuse-devel for your system.

Rebuild:

    ./fuse-rpm

And install

    rpm -Uvh RPMS/$HOSTTYPE/fuse-2.8.5-99.vitki.01.*.$HOSTTYPE.rpm RPMS/$HOSTTYPE/fuse-devel-2.8.5-99.vitki.01.*.$HOSTTYPE.rpm RPMS/$HOSTTYPE/fuse-libs-2.8.5-99.vitki.01.*.$HOSTTYPE.rpm


Build the s3fs-fuse RPMs
------------------------

Build the RPMs:

    ./s3fs-fuse-rpm

And install:

    rpm -Uvh RPMS/$HOSTTYPE/s3fs-fuse-1.77-1.*.$HOSTTYPE.rpm
