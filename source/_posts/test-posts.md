title: openssl 升级
author: John Doe
tags:
  - Linux
categories:
  - Linux
date: 2023-10-29 11:25:00
---
工具： https://github.com/boypt/openssh-rpms

```
yum groupinstall -y "Development Tools"
yum install -y imake rpm-build pam-devel krb5-devel zlib-devel libXt-devel libX11-devel gtk2-devel perl-IPC-Cmd
./pullsrc.sh
这一步报错可以手动下载包
https://ftp.openbsd.org/pub/OpenBSD/OpenSSH/portable/
https://www.openssl.org/source//

./compile.sh
```

```shell
# 本机升级OpenSSH版本
rpm -Uvh el7/RPMS/x86_64/*.rpm
# 删除本机密钥（该操作一定要做）
rm -rf /etc/ssh/ssh_host_*
# 重启sshd服务
systemctl restart sshd
# 查看sshd服务运行状况
systemctl status sshd
# 查看升级后的SSH版本
ssh -V
# 把生成的 rpm 安装包打包
cd el7/RPMS/x86_64
tar -zcvf openssh9.4p1_el7_rpm.tar.gz *.rpm
```

参考链接：
- https://zhuanlan.zhihu.com/p/652906168
- https://bbs.sangfor.com.cn/forum.php?mod=viewthread&tid=261693