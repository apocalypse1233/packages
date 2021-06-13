#
# Copyright (C) 2006-2021 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=vnstat-backup
PKG_VERSION:=0.1
PKG_RELEASE:=1

# PKG_BUILD_DIR:=$(BUILD_DIR)/vnstat-backup-$(PKG_VERSION)

# PKG_FIXUP:=autoreconf
# PKG_INSTALL:=1
# PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/vnstat-backup
  SECTION:=net
  CATEGORY:=Network
  TITLE:=vnstat stats file backup script
  DEPENDS:=+vnstat +vnstati +lftp
endef

define Package/vnstat-backup/description
	vnStat-backup is a tool to make backups of stats files 
	local or remotelly, using ftp.
endef

define Package/vnstat-backup/conffiles
/etc/vnstat_backup.conf
endef

define Package/vnstat-backup/install
	$(INSTALL_DIR) $(1)/etc/init.d $(1)/etc
	$(INSTALL_BIN) ./files/vnstat_backup.init $(1)/etc/init.d/vnstat_backup
	$(INSTALL_CONF) ./files/vnstat_backup.conf $(1)/etc/vnstat_backup.conf
endef

define Package/vnstat-backup/postinst
	#!/bin/sh
	# check if we are on real system
	if [ -z "$${IPKG_INSTROOT}" ]; then
		/etc/init.d/vnstat_backup enable
	fi
	exit 0
endef

$(eval $(call BuildPackage,vnstat-backup))
