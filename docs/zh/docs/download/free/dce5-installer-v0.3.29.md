---
date: 2022-12-14
hide:
  - navigation
---

# DCE 5.0 社区版 v0.3.29

本页可下载 DCE 5.0 社区版的离线安装包和校验文件。

## 下载

| 版本名称         | 安装包                       |
| ---------------- | ---------------------------- |
| offline-centos7-community-v0.3.29-amd64.tar | [:arrow_down: 下载](https://proxy-qiniu-download-public.daocloud.io/DaoCloud_Enterprise/dce5/offline-centos7-community-v0.3.29-amd64.tar) |

## 校验

进入离线安装包下载目录。执行以下命令校验安装包：

```sh
echo "988bf4397f555804fb004a83e01169fd4cfb995d0659170197cab4d07c26aefb6c916ce42c0655d207a2ae7bddd5c28c6c66fc7645c67a174a8919e7e040cbd8" | sha512sum -c
```

校验成功会打印：

```none
offline-centos7-community-v0.3.29-amd64.tar: OK
```

## 安装

成功校验离线包之后，解压缩 tar 包：

```sh
tar -zxvf offline-centos7-community-v0.3.29-amd64.tar
```

然后参阅[社区版安装流程](../../install/community/k8s/online.md#_2)进行安装。

成功安装之后请[申请免费社区体验](../../dce/license0.md)。

## 模块

DCE 5.0 社区版默认包含以下模块：

| 模块     | 介绍                                                              | 最新动态                                                   |
| -------- | ----------------------------------------------------------------- | ---------------------------------------------------------- |
| 全局管理 | 负责用户访问控制、权限、企业空间、审计日志、个性化外观设置等      | [v0.11](../../ghippo/01ProductBrief/release-notes.md#v011) |
| 容器管理 | 管理集群、节点、工作负载、Helm 应用、CRD、命名空间等 K8s 核心功能 | [v0.12](../../kpanda/03ProductBrief/release-notes.md#v012) |
| 可观测性 | 提供丰富的仪表盘、场景监控、数据查询、告警等图文信息              | [v0.11](../../insight/03ProductBrief/releasenote.md#v011)  |

## 更多

- [在线文档](https://docs.daocloud.io/dce/what-is-dce/)
- [报告 bug](https://github.com/DaoCloud/DaoCloud-docs/issues)