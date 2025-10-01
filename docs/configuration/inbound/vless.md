# VLESS

!!! warning ""

    Currently, VLESS does not provide built-in encryption. Please use it with a reliable channel, such as TLS.

VLESS is a stateless lightweight transport protocol that consists of inbound and outbound parts. It can serve as a bridge between Xray clients and servers.
Unlike VMess, VLESS does not rely on system time. The authentication method is still UUID-based.

### InboundConfigurationObject

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

An array representing a group of users approved by the server.
Each item in the array is a user.

#### decryption

Currently, you need to specify `"none"`. It cannot be left empty. If the `decryption` value is not set correctly, you will receive an error message when using Xray or `-test`.

#### fallbacks

An array that contains a series of fallback configurations.

### ClientObject

```json
{
  "id": "5783a3e7-e373-51cd-8642-c83782b807c5",
  "level": 0,
  "email": "",
  "flow": "xtls-rprx-vision"
}
```

#### id

The user ID for VLESS. It can be any string less than 30 bytes or a valid UUID.

Execute `xray uuid -i "custom strings"` to generate the UUID corresponding to a custom string.
Execute `xray uuid` to generate a random UUID.

#### level

The user level that the connection will use to determine the corresponding.

The value of `level` corresponds to the value of policy.level.The default value is 0.

#### email

User email address used to differentiate traffic from different users.

#### flow

Flow control mode used to select the XTLS algorithm.
Additionally, XTLS currently only supports TCP+TLS/Reality.

The following flow control modes are available for inbound protocols:

| mode            | algorithm                           |
|------------------|-----------------------------------------|
|                 | Use regular TLS proxy                |
| xtls-rprx-vision  | Use the XTLS mode, including inner-handshake random padding |
