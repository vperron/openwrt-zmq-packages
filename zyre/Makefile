# Copyright (C) [2011-2012] [TheClashingRocks.org]
#
# Author: Victor Perron <victor@iso3103.net>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=zyre
PKG_VERSION:=master
PKG_REV:=master

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_REV)
PKG_SOURCE_URL:=git://github.com/hintjens/zyre.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/zyre
    MAINTAINER:=victor@iso3103.net
    TITLE:=zyre
    SECTION:=libs
    DEPENDS:=+libuuid +filemq
    CATEGORY:=Libraries
endef

define Package/zyre/description
	ZyRE discovery library implementing ZRE protocol.
endef

TARGET_CFLAGS=-std=c99

define Build/Configure
	( cd $(PKG_BUILD_DIR)/C ; ./autogen.sh );
	( cd $(PKG_BUILD_DIR)/C && CFLAGS="$(TARGET_CFLAGS)" LDFLAGS="$(TARGET_LDFLAGS)" ./configure $(CONFIGURE_ARGS) )
endef


define Build/Compile
	$(call Build/Compile/Default, -C $(PKG_BUILD_DIR)/C )
endef

define Build/Install
	$(call Build/Install/Default, install -C $(PKG_BUILD_DIR)/C )
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib $(1)/usr/include $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(CP) -r $(PKG_BUILD_DIR)/C/include/* $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/zyre/install
	$(INSTALL_DIR) $(1)/usr/lib 
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,zyre))
