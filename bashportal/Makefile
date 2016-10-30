#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bashportal
PKG_VERSION:=0.1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=git://github.com/JAukey/Bash-Portal.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=V0.1

include $(INCLUDE_DIR)/package.mk

define Package/bashportal
	SUBMENU:=Captive Portals
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+nginx +liblua
	TITLE:=Bash script network gateway daemon
	URL:=https://github.com/JAukey/Bash-Portal.git
endef

define Package/bashportal/description
	Bashportal is a simple bash script which provide
	restricted access to an internet connection.
endef

define Package/bashportal/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bash_portal.sh $(1)/usr/bin/bashportal
    
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) files/clientkick.init $(1)/usr/bin/clientkick

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) files/bashportal.init $(1)/etc/init.d/bashportal
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) files/bashportal.config $(1)/etc/config/bashportal

	$(INSTALL_DIR) $(1)/etc/$(PKG_NAME)/html
	$(CP) $(PKG_BUILD_DIR)/html/index.html $(1)/etc/$(PKG_NAME)/html/
	
	$(INSTALL_DIR) $(1)/etc/$(PKG_NAME)/html/images
	$(CP) $(PKG_BUILD_DIR)/html/images/edgelogo.png $(1)/etc/$(PKG_NAME)/html/images
	
	
	$(INSTALL_DIR) $(1)/etc/$(PKG_NAME)/html/lua
	$(CP) $(PKG_BUILD_DIR)/html/lua/portal.lua $(1)/etc/$(PKG_NAME)/html/lua
	
endef

$(eval $(call BuildPackage,bashportal))
