#
#  FreeSwitch mod_amd module
#
#  Makefile created by Zvonimir Buzanic.
#  zvonimir.buzanic@asseco-see.hr
#  2024-02-28
#
# after building mod_amd copy this Makefile and debian directory to mod_amd/deb/
# cd mod_amd/deb/ then run "make deb"

VERSION=1.0.0
RELEASE=2b3a040

NAME=mod-amd
ME=${NAME}-${VERSION}-${RELEASE}
ARCH:=${shell uname -m}
prefix=/usr/local
libdir=/usr/lib/freeswitch/mod
incdir=${prefix}/include
sharedir=${prefix}/share
bindir=${prefix}/bin
pkgdir=${libdir}/pkgconfig
installdir=/etc/freeswitch/autoload_configs/
INSTALL?=install -c
INSTALL_DATA=${INSTALL} -m 644
LIBLIVEINCL=-I..
COMMENT=Asterisk app_amd for FreeSWITCH mod_amd.

clean:
	rm -rf ${ME} mod-amd*.deb

deb: clean
	mkdir -p ${ME}/${libdir} ${ME}/${installdir} ${ME}/${incdir}/mod_amd/ ${ME}/DEBIAN/
	${INSTALL} -m 775 debian/* ${ME}/DEBIAN/
	sed -i -e "s/%%VERSION%%/${VERSION}.${RELEASE}/g" ${ME}/DEBIAN/control
#mod_amd
	${INSTALL} -m 755 ../mod_amd.c ${ME}/${incdir}/mod_amd/mod_amd.c
	${INSTALL} -m 755 ../mod_amd.so ${ME}/${libdir}/mod_amd.so
	${INSTALL} -m 755 ../amd.conf.xml ${ME}/${installdir}/amd.conf.xml
	dpkg-deb --build ${ME}
