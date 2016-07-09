# rpmbuild-znc-external-modules

Create a znc module RPM for RHEL/CentOS.

## Requirements

To download package sources and install build dependencies

    yum -y install rpmdevtools yum-utils

This package requires EPEL for znc development packages

    yum -y install epel-release

## Build process

Available modules

 * colloquy
 * fish
 * palaver
 * push

Select a module to build (example: palaver)

    ZNC_MODULE_BUILD=palaver

To build the package follow the steps outlined below

    git clone https://github.com/linuxhq/rpmbuild-znc-external-modules.git rpmbuild
    mkdir rpmbuild/SOURCES
    spectool -g -R rpmbuild/SPECS/znc-${ZNC_MODULE_BUILD}.spec
    yum-builddep --enablerepo=epel rpmbuild/SPECS/znc-${ZNC_MODULE_BUILD}.spec
    rpmbuild -ba rpmbuild/SPECS/znc-${ZNC_MODULE_BUILD}.spec

## License

BSD

## Author Information

This package was created by [Taylor Kimball](http://www.linuxhq.org).
