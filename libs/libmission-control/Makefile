include $(TOPDIR)/rules.mk

PKG_NAME:=telepathy-mission-control
PKG_VERSION:=4.67
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/mission-control/
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/

define Package/libmisson-control
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libmisson-control
  URL:=http://www.jamesh.id.au/software/libmisson-control/
  DEPENDS:=+libtelepathy
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--libexecdir=/usr/lib/telepathy \
		--disable-tests \
		--disable-keyring \
		--enable-server \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/include/libmcclient/_gen
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libmcclient/*.h \
		$(1)/usr/include/libmcclient/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libmcclient/_gen/*.h \
		$(1)/usr/include/libmcclient/_gen/

	$(INSTALL_DIR) $(1)/usr/include/libmissioncontrol/_gen
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libmissioncontrol/*.h \
		$(1)/usr/include/libmissioncontrol/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libmissioncontrol/_gen/*.h \
		$(1)/usr/include/libmissioncontrol/_gen/

	$(INSTALL_DIR) $(1)/usr/include/mission-control/_gen
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/mission-control/*.h \
		$(1)/usr/include/mission-control/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/mission-control/_gen/*.h \
		$(1)/usr/include/mission-control/_gen/
endef

define Package/libmisson-control/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/lib/telepathy
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/telepathy/* \
		$(1)/usr/lib/telepathy/

	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/share/dbus-1/services
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/dbus-1/services/* \
		$(1)/usr/share/dbus-1/services/
endef

$(eval $(call BuildPackage,libmisson-control))
