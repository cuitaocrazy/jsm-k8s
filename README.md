# JSM kubernetes 部署配置

## docker

`执行环境为macOS或linux`

build docker 镜像执行一下脚本

```bash
build-docker.sh
```

脚本里版本号根据需要更改

## kubernetes

必要条件:

1. kubernetes 节点机上有 jsm 的镜像
2. 或者 docker 资料库中有 jsm 的镜像, 当有时建议修改 deployment.yaml 文件的`imagePullPolicy`为`Always`, 以保证镜像为最新的镜像.

执行一下命令部署:

```bash
kubectl apply -f deployment.yaml
```

删除部署:

```bash
kubectl delete -f deployment.yaml
```

### deployment.yaml

设置正确的 jsm 镜像版本号, 如果需要 latest 版本, 就在 build-docker.sh 里修改

设置正确的环境变量

namespace 根据需要添加, 默认的 namespace 为 default

## 环境变量

| 名称                       | 描述                | 默认值                                      |
| -------------------------- | ------------------- | ------------------------------------------- |
| JDBC_DRIVER                | jdbc 驱动           | oracle.jdbc.driver.OracleDriver             |
| JDBC_URL                   | jdbc URL            | jdbc:oracle:thin:@192.168.125.117:1521:orcl |
| JDBC_USER                  | 数据库用户名        | jsm                                         |
| JDBC_PWD                   | 数据库密码          | anNt                                        |
| JDBC_POOL_MAX_IDLE         | jdbc 最大空闲连接数 | 10                                          |
| JDBC_POOL_MAX_ACTIVE       | jdbc 最大活动连接数 | 40                                          |
| ENCRY_MACHINE_MESSAGE_HEAD |                     | 1234567                                     |
| SERVICE_URL                |                     | http://22.188.197.234:61205/fbasic/         |
| SUPER_POS_URL              |                     | http://22.188.197.234:61205/fbasic/         |
| ENCRY_MACHINE_IP           | 加密机 IP           | 22.188.41.19                                |
| ENCRY_MACHINE_PORT         | 加密机端口          | 8                                           |
| ENCRY_MACHINE_FLAG         |                     | 0                                           |
