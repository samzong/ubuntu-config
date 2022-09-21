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

## docker registry-mirrors 国内加速配置








## docker daemon.json 指定 cgroupdriver

在部署 k8s 时，docker cgroupdriver 的配置, node 和 master 之间不一致，会导致 node join 失败
```json
{
  # ...
  "exec-opts": ["native.cgroupdriver=systemd"],
  # ...
}
```
