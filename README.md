# Shadowsocks(R)/V2Ray subscription decoder/parser

A POSIX compatible shell script to decode and parse Shadowsocks/ShadowsocksR/V2Ray subscription link.

## Requirement:

POSIX compatible shell, `sed`, `curl` or `wget`, `base64`

## Usage

The script accepts either one CLI argument or multiple from pipe. The arguments can be:
- `http(s)://` protocol subscription link which normally contains multiple configs
- A single `ss://` or `ssr://` or `vmess://` protocol link which is a single config
- The downloaded content of subscription link (base64 encoded)

```sh
ssr-decode [ (http|https)://link | (ss|ssr|vmess)://BASE64 | BASE64 | < input.txt ]
```

## Output

The script will generate `*.json` configuration files for each Shadowsocks(R)/V2Ray setup.

- The ShadowsocksR configuration file will be named `ssr-$group-$remarks.json` with `group` normally being the service provider, `remarks` being the description of this setup.
- The Shadowsocks configuration file will be named `ss-$server-$port.json`.
- The V2Ray configuration file will be named `v2ray-$ps.json` with `ps` normally being the description.
