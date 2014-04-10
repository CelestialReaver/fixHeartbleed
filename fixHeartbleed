#!/bin/bash
#########################################
#
# The purpose of this script is to fix
# the Heartbleed vulnerability on Red Hat
# and CentOS systems (specifically 6.x).
#
# Security Advisory:
# CVE-2014-0160
#
# Test if site is vulnerable:
# http://filippo.io/Heartbleed/
#
# PVG - 2014
#
#########################################

echo
echo -e "\E[5;37;41m<3 HEARTBLEED FIX <3\033[0m"

## Install required files to build OpenSSL 1.0.1g
echo
echo -e "\E[5;37;44mInstalling required tools to build openssl-1.0.1g\033[0m"
yum -y groupinstall "Development tools" > /dev/null 2>&1
yum -y install wget > /dev/null 2>&1

## Download patched version of OpenSSL
echo
echo -e "\E[5;37;44mDownloading openssl-1.0.1g\033[0m"
cd /tmp > /dev/null 2>&1
wget http://www.openssl.org/source/openssl-1.0.1g.tar.gz > /dev/null 2>&1

## Untar, build and install new OpenSSL-1.0.1g
echo
echo -e "\E[5;37;44mUntar-ing, building and installing openssl-1.0.1g\033[0m"
tar -zxf openssl-1.0.1g.tar.gz > /dev/null 2>&1
cd openssl-1.0.1g > /dev/null 2>&1
./config --prefix=/usr --openssldir=/usr/local/openssl shared > /dev/null 2>&1
make > /dev/null 2>&1
make install > /dev/null 2>&1

## Restart httpd to use new OpenSSL-1.0.1g
echo
echo -e "\E[5;37;44mRestarting httpd so it will use openssl-1.0.1g\033[0m"
/etc/init.d/httpd restart > /dev/null 2>&1

## Check to see if vulnerability stil exist
echo
echo -e "\E[5;37;44mCOMPLETE! Check site at http://filippo.io/Heartbleed/ to verify fix\033[0m"

echo
sleep 5
