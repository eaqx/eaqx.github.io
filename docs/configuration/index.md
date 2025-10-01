# Overview

The configuration file of Xray is in JSON format, and the configuration format for the client and server is the same, except for the actual configuration content.

## Form:

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

## Basic Configuration Modules

### version

This setting controls which versions this config can run on. It helps prevent the config from running on unintended client versions when shared. The client will check at runtime whether the current version meets this requirement.

### log

Log configurations, controlling how Xray emits logs.

### api

Provides some API interfaces for calling remotely.

### dns

Configures the built-in DNS server. System DNS will be used if not configured.

### routing

Configures routing. Specify rules to route connections through different outbounds.

### policy

Local policy configurations, specifying different user levels and corresponding policies.

### inbounds

An array of inbound connection configurations

### outbounds

An array of outbound connection configurations.

### transport

Configures how Xray establishes and uses network connections to other servers.

### stats

Configures traffic statistics.

### reverse

Configures the built-in reverse proxy. You can forward server traffic to the client, effectively achieving reverse proxying

### fakedns

FakeDNS configuration. Can be used with a transparent proxy to obtain the actual domains.

### metrics

Metrics configuration. A more straightforward (and hopefully better) way to export metrics.

### observatory

Background connection observation. Detect the connection status of outbound proxies.

### burstObservatory

Concurrent connection observation. Detect the connection status of outbound proxies.