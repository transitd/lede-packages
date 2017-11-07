
include $(TOPDIR)/rules.mk

PKG_NAME:=transitd
PKG_VERSION:=0.1.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/transitd/transitd.git
PKG_SOURCE_VERSION:=master

PKG_MAINTAINER:=Alex R <alex@maximum.guru>
PKG_LICENSE=MIT

include $(INCLUDE_DIR)/package.mk

define Package/transitd
  SUBMENU:=VPN
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Transit Daemon
  URL:=https://transitd.org/
  DEPENDS:=+lua +luasocket +cgilua +lua-cjson +lua-inifile +lua-xavante +lua-wsapi-xavante +jsonrpc4lua +lua-sha2 +lua-bencode +dkjson +lua-bit32 +luasql-sqlite3 +lua-alt-getopt +luaproc +lua-coxpcall +lua-copas +ipip +kmod-ip6-tunnel +kmod-iptunnel4 +kmod-iptunnel6 +ip-full -ip -ping -ping6 +iputils-ping +iputils-ping6 +cjdns
endef

define Package/transitd/description
	Transit Daemon is an automated Internet gateway publishing tool for community networks.
endef

define Build/Compile
endef

define Package/transitd/install
	$(INSTALL_DIR) \
		$(1)/opt/transitd \
		$(1)/usr/bin \
		$(1)/etc/init.d \
		$(1)/etc/uci-defaults
	
	$(CP) $(PKG_BUILD_DIR)/src $(1)/opt/transitd/
	$(CP) $(PKG_BUILD_DIR)/transitd.conf.sample $(1)/opt/transitd/
	$(CP) $(PKG_BUILD_DIR)/LICENSE $(1)/opt/transitd/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lede/usr/bin/* $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lede/etc/init.d/* $(1)/etc/init.d/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lede/etc/uci-defaults/* $(1)/etc/uci-defaults/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lede/opt/transitd/*.sh $(1)/opt/transitd/
	$(CP) $(PKG_BUILD_DIR)/lede/opt/transitd/*.lua $(1)/opt/transitd/
endef

$(eval $(call BuildPackage,transitd))
