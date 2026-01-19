#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=qmi-wwan-q
PKG_VERSION:=20230915
PKG_RELEASE:=1

PKG_MAINTAINER:=Chen Minqiang <ptpt52@gmail.com>
PKG_LICENSE:=GPL-2.0-only
PKG_BUILD_PARALLEL:=1
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

define KernelPackage/qmi-wwan-q
  SUBMENU:=Network Support
  SECTION:=net
  CATEGORY:=Kernel modules
  TITLE:=QMI WWAN QMAP driver
  FILES:=$(PKG_BUILD_DIR)/qmi_wwan_q.ko
  AUTOLOAD:=$(call AutoProbe,qmi-wwan-q)
  DEPENDS:=+kmod-usb-net-qmi-wwan
  KCONFIG:=
endef

define KernelPackage/qmi-wwan-q/description
  QMI WWAN QMAP driver for Qualcomm MSM based 3G and LTE modems.
  This module allows multiplexing network interfaces with Qualcomm QMAP protocol.
endef

define Build/Prepare
	# You can add prepare steps here, if necessary
	$(Build/Prepare/Default)
endef

define Build/Compile
	$(KERNEL_MAKE) M="$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="$(EXTRA_CFLAGS)" \
		$(PKG_EXTRA_KCONFIG) \
		modules
endef

define KernelPackage/qmi-wwan-q/install
	# An optional install phase if you need to handle additional steps
	$(call KernelPackage/Install,$(1))
endef

$(eval $(call KernelPackage,qmi-wwan-q))
