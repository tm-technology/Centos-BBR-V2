# Centos-BBR-V2

wget https://github.com/pkpkgtr1/Centos-BBR-V2/releases/download/v1.0/bbr_kernel.zip
yum -y unzip & unzip bbr_kernel.zip
yum -y localinstall *
grub2-set-default 0
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control = bbr2" >> /etc/sysctl.conf
echo "net.ipv4.tcp_ecn = 1" >> /etc/sysctl.conf   # 开启ecn (可选)
sysctl -p
rm kernel-5.2.0_rc3+-1.x86_64.rpm
rm kernel-headers-5.2.0_rc3+-1.x86_64.rpm
reboot
