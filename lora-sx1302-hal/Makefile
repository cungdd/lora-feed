#
# Copyright (C) 2021 Xue Liu <liuxuenetmail@gmail>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lora-sx1302-hal
PKG_VERSION:=2.1.0
PKG_RELEASE:=1

#PKG_SOURCE_URL:=https://codeload.github.com/Lora-net/sx1302_hal/tar.gz/V$(PKG_VERSION)?
#PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
#PKG_HASH:=1a0447d5e8183d08e6dce5f739f6872b9c57824b98f4078830d5ee21b15782c1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/cungdd/sx1302_hal
PKG_SOURCE_VERSION:=f52ca4169cc44e6e56c8d152de12c8c649fb6c15
PKG_HASH:=d1a3a9ebd07a9a0d6f71438bcf1096da3575c17b8a141effec3f3beff2b5f51a
# PKG_SOURCE_URL:=https://github.com/thinpv/sx1302_hal
# PKG_SOURCE_VERSION:=0c5139edab95db57e3251e915d938b9de98d2735

PKG_MAINTAINER:=Xue Liu <liuxuenetmail@gmail.com>
PKG_LICENSE_FILES:=LICENSE
#PKG_BUILD_DIR:=$(BUILD_DIR)/sx1302_hal-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libsx1302
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Driver/HAL library for Semtech SX1302
  URL:=https://www.semtech.com/products/wireless-rf/lora-gateways/sx1302
  DEPENDS:=+kmod-spi-dev
endef

define Package/libsx1302/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/packet_forwarder/lora_pkt_fwd $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/packet_forwarder/global_conf.json.sx1250.AS923.USB $(1)/etc/global_conf.json
endef

$(eval $(call BuildPackage,libsx1302))
