FROM quay.io/centos/centos:centos7.9.2009
RUN yum -y install which git epel-release kernel-devel @development rpm-build rpmdevtools mc vim-common wget openssh-server net-tools systemd-devel xz-devel sudo
RUN yum -y update
RUN yum -y install rust cargo
WORKDIR /root/
