# Copyright (C) [2013]
#
# Author: Victor Perron <victor@iso3103.net>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=czmq
PKG_VERSION:=1.3.3-pre
PKG_REV:=a7cbcba3b40da5b6bb71b7c1b71fa5330c296261
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=git://github.com/zeromq/czmq.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/czmq
    MAINTAINER:=victor@iso3103.net
    TITLE:=czmq
    SECTION:=libs
    DEPENDS:=+zeromq
    CATEGORY:=Libraries
endef

define Package/czmq/description
	Handy C Wrapper for zeromq.
endef

TARGET_CFLAGS = -std=c99

define Build/Configure
	( cd $(PKG_BUILD_DIR); ./autogen.sh );
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	$(INSTALL_DIR) \
		$(1)/usr/lib 	\
		$(1)/usr/include \
		$(1)/usr/lib/pkgconfig
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/* \
		$(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/* \
		$(1)/usr/include/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig \
		$(1)/usr/lib/

endef

define Package/czmq/install
	$(INSTALL_DIR) $(1)/usr/lib 
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/

endef

$(eval $(call BuildPackage,czmq))
