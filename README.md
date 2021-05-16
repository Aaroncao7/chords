# Deployer for BUAA

## CLI

```bash
# 帮助
./bin/execute --help
./bin/execute create-network --help

# 执行命令
./bin/execute create-network '{"networkName":"string","initOrgName":"string","initOrgAliasName":"string","initPeerInfo":[{"isAnchor":true,"nodeName":"string","nodeAliasName":"string","serverName":"string"}],"companyName":"string"}'

# Sync 命令
./bin/execute sync syncPrometheusPorts
```

Sync Jobs:

- syncNetworks
- syncPrometheusPorts
- syncContainers
- syncNetworkChannels

# 如需单独编译 Explorer，使用命令：

# 1.2 为版本号

docker build -f ./Dockerfile . -t whitematrixlab/deployer-app:latest

````

```bash
docker tag whitematrixlab/deployer-app:latest registry.cn-zhangjiakou.aliyuncs.com/whitematrixlab/deployer-app:1.2
````

```
docker push registry.cn-zhangjiakou.aliyuncs.com/whitematrixlab/deployer-app:1.2
```

部署到阿里云 k8s 集群

```
kubectl apply -f k8s-alicloud/k8s-alicloud/create-network-job.yml
```
# deployment job

部署job yml 在 k8s-alicloud目录下
需要更改的参数
image：镜像的版本号
command：所要执行的部署任务 ['./bin/execute', 'org-join-channel']
env: 环境变量
- name: arg
  value: '{"channelId": "newchannel","orgName": "neworg","networkName": "newnet","companyName": "string"}'
需要修改参数
