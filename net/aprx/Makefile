#
# Copyright (C) 2008-2016 OpenWrt.org
# adapted by pa0esh
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=aprx
PKG_REV:=""
PKG_VERSION:=2.9.0
PKG_RELEASE:=Stable
PKG_PROTO_NAME:=git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
#PKG_SOURCE_URL:=http://thelifeofkenneth.com/aprx/release/

PKG_SOURCE_URL:=https://github.com/PhirePhly/aprx

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_PROTO:=$(PKG_PROTO_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/aprx
  SECTION:=net
  CATEGORY:=Network
  TITLE:=APRS RX & TX igate / Digipeater PhirePhly version 2.8.2 Github
  URL:=https://github.com/PhirePhly/aprx
  DEPENDS:=+libpthread

endef

define Package/aprx/description
	This daemon listens for traffic on the specified serial interfaces.
	It then forwards appropriate packets to APRS-IS servers.
	It also can act as a digipeater
endef

CONFIGURE_ARGS += \
	--with-embedded \

define Package/aprx/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/aprx.init $(1)/etc/init.d/aprx
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/aprx.conf $(1)/etc/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/aprx $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/aprx-stat $(1)/usr/sbin/
endef

define Package/aprx/conffiles
/etc/aprx.conf
endef

$(eval $(call BuildPackage,aprx))

