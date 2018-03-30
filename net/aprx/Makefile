#
# Copyright (C) 2008-2018 OpenWrt.org
# adapted by pa0esh for Openwrt Lede
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=aprx
PKG_REV:=""
PKG_VERSION:=2.9.0
PKG_RELEASE:=Stable
PKG_PROTO_NAME:=git
PKG_SOURCE_URL:=https://github.com/videobuff/openwrt-aprx.git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$PKG_RELEASE.tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_PROTO:=$(PKG_PROTO_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/aprx
  SECTION:=net
  CATEGORY:=Network
  TITLE:=APRS RX & TX igate / Digipeater PhirePhly version 2.9.0 Github
  URL:=https://github.com/videobuff/aprx.git
  DEPENDS:=+libpthread
endef

define Package/aprx/description
	This daemon listens for traffic on the specified serial interfaces.
	It then forwards appropriate packets to APRS-IS servers.
endef

CONFIGURE_ARGS += \
	--with-embedded \

# Package preparation instructions; create the build directory and copy the source code. 
# The last command is necessary to ensure our preparation instructions remain compatible with the patching system.
define Build/Prepare
        mkdir -p $(PKG_BUILD_DIR)
        cp $(SOURCE_DIR)/* $(PKG_BUILD_DIR)
        $(Build/Patch)
endef

# Package build instructions; invoke the target-specific compiler to first compile the source file, and then to link the file into the final executable
define Build/Compile
        $(TARGET_CC) $(TARGET_CFLAGS) -o $(PKG_BUILD_DIR)/helloworld.o -c $(PKG_BUILD_DIR)/helloworld.c
        $(TARGET_CC) $(TARGET_LDFLAGS) -o $(PKG_BUILD_DIR)/$1 $(PKG_BUILD_DIR)/helloworld.o
endef

# Package install instructions; create a directory inside the package to hold our executable, and then copy the executable we built previously into the folder
define Package/aprx/install
        $(INSTALL_DIR) $(1)/usr/bin
        $(INSTALL_BIN) $(PKG_BUILD_DIR)/helloworld $(1)/usr/bin
endef


$(eval $(call BuildPackage,aprx))
