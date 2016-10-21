# K8s with flannel ansible 常用命令 

## 全局环境变量

[group_vars](group_vars) 根据实际需求修改相应环境变量

## K8s 组件和配置文件更新

* kubernetes 二进制同步目录：
    * *.*.*.*
    * /usr/local/src/k8s_bin

### K8s + flannel First Time Install

* All

ansible-playbook -i inventory/ci_server all.yml

### K8s 组件更新

* master

更新 Kubernetes master 程序和配置：

```
ansible-playbook -i inventory/ci_server master-bin.yml
ansible-playbook -i inventory/ci_server master-conf.yml
```

* nodes

更新全部节点 Kubernetes 程序和配置：

```
ansible-playbook -i inventory/ci_server nodes-bin.yml     # 更新全部 Kubernetes 节点程序
ansible-playbook -i inventory/ci_server nodes-conf.yml    # 更新全部 Kubernetes 节点配置文件
```

更新指定节点 Kubernetes 程序和配置：

```
ansible-playbook -i inventory/ci_server --limit=10.199.198.189 nodes-bin.yml      # 更新指定 Kubernetes 节点 Kubernetes 程序
ansible-playbook -i inventory/ci_server --limit=10.199.198.189 nodes-conf.yml     # 更新指定 Kubernetes 节点配置文件
```

## K8s 新增节点 

添加 K8s 指定节点：

```
ansible-playbook -i inventory/ci_server --limit=10.199.198.189 nodes.yml --tags=
```
