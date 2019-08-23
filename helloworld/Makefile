#
# Copyright (C) 2015-2018 neil.zhang@siflower.com.cn
#
# sifiower Software.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hello_world
PKG_VERSION:=1
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define Package/hello_world
SECTION:=utils
CATEGORY:=Utilities
TITLE:=hello_world.
MAINTAINER:=Star jiang <star.jiang@siflower.com.cn>
DEPENDS:=+libc +libpthread +librt +libm +libubus
endef

define Package/hello_world/description
print hello_world.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		CFLAGS="$(TARGET_CFLAGS) -Wall -Wno-unused-but-set-variable -Wno-unused-function" \
		LDFLAGS="$(TARGET_LDFLAGS) -lpthread -lc -lm"
endef

define Package/hello_world/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/hello_world
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/hello_world $(1)/usr/bin
endef


$(eval $(call BuildPackage,hello_world))
