---
title: mongo
date: 2021-03-18 19:23:11
categories:
  - 数据库
tags:
  - db
---
## 客户端
   mongodb compass
   
## 功能
1 复制集 -->  高可用    
2 数据分发 读写分离 异地容灾
3 复制集最多50个 7个选举节点
4 数据写在主节点 增加节点不会提升写性能
5 复制集创建   init+add 节点    slaveok方法使得从节点可读


## 工具
1 --Altas 云托管mongodb  --free test  
2 --mongodb ops manager 集群管理平台
3 --mongodb chart 图形化工具  dashbord(自动生成代码嵌入html)


## 数据库设计
1 同类小数据写入
2 列变行 合并同类字段为列表
3 有统计需求 可增加统计字段 避免大量数据参与计算
4 writeConcern 写入节点数  避免单点故障  journal 如何算写入成功
5 节点选择优先级 主从 就近 |  tag 分类 按tag组获取数据
6 隔离性参数 数据的一致性问题 性能与准确性平衡
7 abortsession  mongodb针对错误的事务和提交会发起重试 所以最好重启会话 
8 changestream 触发器机制  --满足数据多节点提交才能开启 避免不一致误触发
9 域名替代节点   分片集群提供负载均衡

