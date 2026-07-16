# luci-app-ddns-go

Native LuCI management and OpenWrt packaging for the
[ysuolmai/ddns-go](https://github.com/ysuolmai/ddns-go) router fork.

The OpenWrt build does not expose the upstream standalone web interface.
LuCI is the only browser-facing management surface and communicates with the
daemon through a local Unix socket protected by rpcd ACLs.

## Packages

- `ddns-go`: provider engine, procd service and persistent configuration
- `luci-app-ddns-go`: native LuCI provider editor, status, manual update and logs

Both `/etc/config/ddns-go` and `/etc/ddns-go/ddns-go-config.yaml` are declared
as package configuration files and are retained by sysupgrade.

## OpenWrt feed

```text
src-git ddnsgo https://github.com/ysuolmai/luci-app-ddns-go.git
```

```sh
./scripts/feeds update ddnsgo
./scripts/feeds install -a -p ddnsgo
make menuconfig
```
