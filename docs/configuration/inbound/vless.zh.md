# VLESS

!!! warning ""

    目前 VLESS 没有自带加密，请用于可靠信道，如 TLS。

!!! note ""

    VLESS 是一个无状态的轻量传输协议，它分为入站和出站两部分，可以作为 Xray 客户端和服务器之间的桥梁。
    不同于 VMess，VLESS 不依赖于系统时间，认证方式同样为 UUID。

### 入站配置

```json
{
  "clients": [
    {
      "id": "5783a3e7-e373-51cd-8642-c83782b807c5",
      "level": 0,
      "email": "",
      "flow": "xtls-rprx-vision",
      "reverse": {}
    }
  ],
  "decryption": "none",
  "fallbacks": [
    {
      "dest": 80
    }
  ]
}
```

#### clients

一个数组，代表一组服务端认可的用户，其中每一项为一个用户。

#### decryption

现阶段需要填 `"none"`，不能留空。若未正确设置 decryption 的值，使用 Xray 或 -test 时会收到错误信息。

#### fallbacks

一个数组，包含一系列回落分流配置。

### 客户端配置

```json
{
  "id": "5783a3e7-e373-51cd-8642-c83782b807c5",
  "level": 0,
  "email": "",
  "flow": "xtls-rprx-vision"
}
```

#### id

VLESS 的用户 ID，可以是任意小于 30 字节的字符串, 也可以是一个合法的 UUID.

执行 `xray uuid -i "自定义字符串"` 生成自定义字符串所映射的的 UUID.
执行 `xray uuid` 生成随机的 UUID.

#### level

用户等级，连接会使用这个用户等级对应的本地策略。

level 的值, 对应 policy.level 的值，默认为 0。

#### email

用户邮箱，用于区分不同用户的流量。

#### flow

流控模式，用于选择 XTLS 的算法。
目前 XTLS 仅支持 TCP+TLS/Reality

入站协议中有以下流控模式可选：

| 模式            | 算法                                 |
|------------------|-----------------------------------------|
|                 | 使用普通 TLS 代理                    |
| xtls-rprx-vision  | 使用 XTLS 模式，包含内层握手随机填充 |
