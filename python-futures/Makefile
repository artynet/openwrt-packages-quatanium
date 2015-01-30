#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=futures
PKG_VERSION:=2.2.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/f/futures/
PKG_MD5SUM:=310e446de8609ddb59d0886e35edb534
PKG_BUILD_DEPENDS:=python python-setuptools

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-futures
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-futures
	URL:=https://pypi.python.org/pypi/futures
	DEPENDS:=+python
endef

define Package/python-futures/description
	Backport of the concurrent.futures package from Python 3.2
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix=/usr --root=$(PKG_INSTALL_DIR), \
		PYTHONPATH=$(PYTHON_LIB_DIR):$(STAGING_DIR_ROOT)/$(PYTHON_PKG_DIR); \
		)
endef

define Package/python-futures/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-futures))