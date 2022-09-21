# ubuntu-config

## 使用之前

### 关闭 swap 分区

 修改 /etc/fstab ，注释最后一行，然后重启系统

```sh
# vim /etc/fstab
# reboot
```

### 调整主机名

```sh
# hostnamectl set-hostname new_hostname    # 永久修改

# hostname    # 查询当前主机名
```

> p.s. 主要把新主机名添加到 `/etc/hosts`

```sh
echo "127.0.0.1 new_hostname" >> /etc/hosts
```

### 调整时区

根据各自的时区调整，设定为主要的时区

```sh
# timedatectl list-timezones   # 查看全部时区
# timedatectl set-timezone "Asia/Shanghai"    # 指定时区
# timedatectl    # 获取当前时区信息
```

可选方式二:

```sh
sudo cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

## docker 安装源

这里替换到 docker 的 安装源，保证安装合适和后续更新

```sh
# step 1: 安装必要的一些系统工具
sudo apt-get update
sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common

# step 2: 安装GPG证书
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -

# Step 3: 写入软件源信息
sudo add-apt-repository "deb http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"

# Step 4: 更新并安装 Docker-CE
sudo apt-get -y update
sudo apt-get -y install docker-ce docker-ce-cli containerd.io
```


