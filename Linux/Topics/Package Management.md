# Package Management 
Package Management is a way of installing and maintaining software packages on the linux system. A package is essentialy an archive file that contains the exeutable file, configuration settings and dependancy information. Debian created *.deb* or *DEB* packaging format and Red Hat Linux created *.rpm* or *RPM (Red Hat Package Manager)*.

### How does the package Manager work?
The package manager works with software repositories by using the metadata files. The metadata files contain information about the packages, such as: name of the package, version number and description of the package. Whenever a package is downloaded, the metadata files are read first to get the latest version of the package avaliable and download any dependecy that is needed along with the package.

## Packaging System
There are 3 distribution families that are covered by the LFCS certifcation and each uses a different packaging systems. They also have different high and low packaging tools. They are:
- *Debian* = `*.deb`, low `dpkg` and high `apt-get/aptitude`
- *CentOS* = `*.rpm` , low `rpm` and high `yum`
- *openSUSE* = `*.rpm` , low `rpm` and high `zypper`
They are not compatible with each other.


### Low Level tools
- Low level package tools work directly with the compilied files (*.deb or *.rpm).
- Normally used when the high level tool is unable to locate the package in the repository.
- `dpkg -i file.deb`: install and updates the package using the complied file.
- `dpkg -l`: list the current installed packages.
- `dpkg -l | grep <specific package>`: To find a specific package.
- `dpkg --status <package_name>`: Another way of checking if the package is installed.


### High Level Tools
- High level package tools work directly with repositories.
- `apt-install` or `apt-update`: install or update the packages. will often prompt the user to confirm the installation after dependncies resolutions.
- `sudo aptitude install nmap`: example of aptitiude can be used to install the package with all it's dependencies.
- `apt remove/purge <package_name>`: remove a package from the system.
- `apt show birthday`: show information about a package named birthday

## Points to Remember
- The *make* command is used to complied the software.
- Idconfig tool is used to update the *id.so.cache file*.
- Dynamic linking creates smaller executable files, unlike static linking which complies libraries into executables.
- Spec file has the compilation option. 
- A Makefile is used to complie source code not in RPM format
- `dpkg --install`: installs the package
- `dpkg -P`: Removes the package.
- The *dselect* tool uses a characterbased graphic interface instead of a command-line interface.
- The source for *apt-get* are stored in the sources.list file
- `dpkg -autoclean`: removes old package that are no longer available.
- `rpm -q`: used to query for a specific package with RPM
- The behaviour of a program can be altered, by modifying the source code.
- Don't use both RPM and Debian package managers. Pick one and stay with it, as they are incompatabile.
- `rpm -ivh megaprog.rpm`: if the package exists, install it.
