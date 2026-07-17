include $(TOPDIR)/rules.mk

PKG_NAME:=ddns-go
PKG_VERSION:=6.17.1.1
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ysuolmai/ddns-go.git
PKG_SOURCE_VERSION:=40cda8eac5856275bbf68c3373a5d95589b143f1
PKG_MIRROR_HASH:=skip

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=ysuolmai
PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/jeessy2/ddns-go/v6
GO_PKG_LDFLAGS_X:=main.version=6.17.1-openwrt.1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/ddns-go
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  TITLE:=DDNS-GO engine for native LuCI management
  URL:=https://github.com/ysuolmai/ddns-go
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
  USERID:=ddns-go:ddns-go
endef

define Package/ddns-go/description
  DDNS-GO provider engine with a local-only OpenWrt management API.
endef

define Package/ddns-go/conffiles
/etc/config/ddns-go
/etc/ddns-go/ddns-go-config.yaml
endef

define Package/ddns-go/install
	$(call GoPackage/Package/Install/Bin,$(1))
	$(INSTALL_DIR) $(1)/etc/init.d $(1)/etc/config $(1)/etc/ddns-go
	$(INSTALL_BIN) ./files/ddns-go.init $(1)/etc/init.d/ddns-go
	$(INSTALL_CONF) ./files/ddns-go.config $(1)/etc/config/ddns-go
	$(INSTALL_CONF) ./files/ddns-go-config.yaml $(1)/etc/ddns-go/ddns-go-config.yaml
endef

define Package/ddns-go/postinst
#!/bin/sh
[ -n "$${IPKG_INSTROOT}" ] || /etc/init.d/ddns-go enable
exit 0
endef

$(eval $(call GoBinPackage,ddns-go))
$(eval $(call BuildPackage,ddns-go))
