# luci-app-ddns-go

这是 [ysuolmai/ddns-go](https://github.com/ysuolmai/ddns-go) 路由器版本的
原生 LuCI 管理器和 OpenWrt 软件包。

路由器版本不开放上游独立 Web 页面，也没有第二套账号密码。浏览器只访问
LuCI；rpcd 在 ACL 控制下通过本机 Unix Socket 管理 ddns-go daemon。

仓库包含：

- `ddns-go`：DNS Provider 引擎、procd 服务和持久化配置
- `luci-app-ddns-go`：原生 LuCI 服务商编辑、状态、立即更新和日志页面

`/etc/config/ddns-go` 和 `/etc/ddns-go/ddns-go-config.yaml` 均由软件包声明为
配置文件，sysupgrade 会自动保留。

作为 feed 引入：

```text
src-git ddnsgo https://github.com/ysuolmai/luci-app-ddns-go.git
```

```sh
./scripts/feeds update ddnsgo
./scripts/feeds install -a -p ddnsgo
make menuconfig
```
