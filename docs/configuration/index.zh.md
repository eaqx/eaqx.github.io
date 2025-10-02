# 概述

!!! note

    Xray 的配置文件为 json 格式, 客户端和服务端的配置格式相同, 仅实际的配置内容不同。

### 形式:

```json
{
  "vsersion": {},
  "log": {},
  "api": {},
  "dns": {},
  "routing": {},
  "policy": {},
  "inbounds": [],
  "outbounds": [],
  "transport": {},
  "stats": {},
  "reverse": {},
  "fakedns": {},
  "metrics": {},
  "observatory": {},
  "burstObservatory": {}
}
```

### 基础配置模块

#### version

控制该 config 可以运行的版本，当分享 config 时防止在不期望的客户端版本意外运行，运行时客户端将会检查当前版本是否匹配该要求。

#### log

日志配置，控制 Xray 输出日志的方式。

#### api

提供了一些 API 接口供远程调用。

#### dns

内置的 DNS 服务器. 如果没有配置此项，则使用系统的 DNS 设置。

#### routing

路由功能。可以设置规则分流数据从不同的 outbound 发出。

#### policy

本地策略，可以设置不同的用户等级和对应的策略设置。

#### inbounds

一个数组，每个元素是一个入站连接配置。

#### outbounds

一个数组，每个元素是一个出站连接配置。

#### transport

用于配置 Xray 其它服务器建立和使用网络连接的方式。

#### stats

用于配置流量数据的统计。

#### reverse

反向代理。可以把服务器端的流量向客户端转发，即逆向流量转发。

#### fakedns

FakeDNS 配置。可配合透明代理使用，以获取实际域名。

#### metrics

metrics 配置。更直接的统计导出方式。

#### observatory

后台连接观测。探测出站代理的连接状态。

#### burstObservatory

突发连接观测。探测出站代理的连接状态。


