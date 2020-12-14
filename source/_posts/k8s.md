---
title: k8s
date: 2019-10-10 14:30:44
categories:运维
tags:容器
description: kubernetes笔记
---

1 Kubernetes概述
 - 用于管理多个主机容器化应用,让容器化部署简单高效,自主管理提供不间断服务
 - 
 
2 名词解释
 - Pod
    ```
   1 k8s最小部署单位 代表集群上运行一个进程
   2 运行一至多个容器,提供存储空间、网络和控制策略 
   3 存在生命周期,依赖controller 调度
    ```
 - Labels
    ```
   1 标示对象特殊意义,划分特定组
    ```
 - Namespace
    ```
   1 资源和对象的集合,用于在项目中划分不同的系统对象
    ```
 - Replication Controller
    ```
   1 配置策略管控pod   
    ```
 - Node
    ```
   1 虚拟机或者物理机,运行pod,提供基础环境(docker kubelet kube-proxy)
    ```
 - ReplicaSets
    ```
   1 优化版Replication Controller 支持更多的选择器
    ```
 - Service
   ```
   1 抽象化后端服务
   ```
 - Volumes
   ```
   1 数据持久化和数据共享
   ```
 - Deployment
   ```
   1 资源对象类型,强调更新
   ```
 - Secret
   ```
   1 解决敏感信息配置问题
   ```
 - StatefulSets
   ```
   1 处理有状态应用,强调顺序执行
   ```
 - DaemonSets
   ```
   1 每个Node都要运行
   ```
 - Service Account
   ```
   1 方便Pod里面的进程调用Kubernetes API或其他外部服务
   ```   
 - CronJob
   ```
   1 定时任务
   ```     
 - Job
   ```
   1 一次性任务
   ```
 - Security Context & PSP
   ```
   1 限制不可信容器行为
   2 PSP -- 集群级别的安全策略
   ```
 - Resource Quotas
   ```
   1 资源限制
   ```   
 - Network Policy
   ```
   1 网络控制策略
   ```   
 - Ingress
   ```
   1 可以给service提供集群外部访问的URL、负载均衡、SSL终止、HTTP路由等
   ```   
 - ConfigMap
   ```
   1 用于保存配置数据 --更方便处理不敏感信息
   ```      
 - PodPreset
   ```
   1 给指定标签的Pod注入额外的信息,如环境变量,存储卷等
   ```
 ## 核心组件
 ```

    etcd保存了整个集群的状态;
    apiserver提供了资源操作的唯一入口,并提供认证,授权,访问控制,API注册和发现等机制;
    controller manager负责维护集群的状态,比如故障检测,自动扩展,滚动更新等;
    scheduler负责资源的调度,按照预定的调度策略将Pod调度到相应的机器上;
    kubelet负责维护容器的生命周期,同时也负责Volume(CVI)和网络(CNI)的管理;
    Container runtime负责镜像管理以及Pod和容器的真正运行(CRI);
    kube-proxy负责为Service提供cluster内部的服务发现和负载均衡;
    kube-dns负责为整个集群提供DNS服务;
    Ingress Controller为服务提供外网入口;
    Heapster提供资源监控;
    Dashboard提供GUI;
    Federation提供跨可用区的集群;
    Fluentd-elasticsearch提供集群日志采集,存储与查询;
 
 ```








```
kubeadm 未指定init 参数  造成网络问题
edit /etc/kubernetes/manifests/kube-controller-manager.yaml
at command ,add
--allocate-node-cidrs=true
--cluster-cidr=10.244.0.0/16
then,reload kubelet
```