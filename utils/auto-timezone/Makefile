include $(TOPDIR)/rules.mk

PKG_NAME:=auto-timezone
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_MAINTAINER:=Renn Akaza <openwrt.org-auto-timezone@akaza.ren>
PKG_LICENSE:=GPL-3.0-or-later

include $(INCLUDE_DIR)/package.mk

define Package/auto-timezone
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Auto set timezone by IP
  PKGARCH:=all
	DEPENDS:=+zoneinfo-all
endef

define Package/auto-timezone/description
Hotplug script to automatically configure the timezone UCI settings based on the IP address.

The user needs to set their own endpoint to get the IANA timezone string, e.g.:
	uci set auto-timezone.config.endpoint="https://domain.tld/json"
	uci commit
endef

define Build/Compile
endef

define Package/auto-timezone/install
	$(INSTALL_DIR) $(1)/etc/hotplug.d/iface/
	$(INSTALL_DATA) ./files/99-auto-timezone $(1)/etc/hotplug.d/iface/
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/auto-timezone.config $(1)/etc/config/auto-timezone
endef

$(eval $(call BuildPackage,auto-timezone))
