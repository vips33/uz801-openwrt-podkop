include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

PKG_NAME:=fbtft-gc9107
PKG_RELEASE:=1

define KernelPackage/fbtft-gc9107
  SUBMENU:=Video Support
  TITLE:=MF68E ST7735S Framebuffer Driver (fbtft)
  DEPENDS:=@TARGET_msm89xx +kmod-backlight
  KCONFIG:= \
    CONFIG_FB=y \
    CONFIG_FB_BACKLIGHT=y \
    CONFIG_FB_DEFERRED_IO=y \
    CONFIG_FB_SYS_FILLRECT=y \
    CONFIG_FB_SYS_COPYAREA=y \
    CONFIG_FB_SYS_IMAGEBLIT=y \
    CONFIG_FB_SYS_FOPS=y \
    CONFIG_FB_DMAMEM_HELPERS=y \
    CONFIG_BACKLIGHT_CLASS_DEVICE=y \
    CONFIG_BACKLIGHT_PWM=y \
    CONFIG_FONTS=y \
    CONFIG_FONT_8x16=y \
    CONFIG_FRAMEBUFFER_CONSOLE=y \
    CONFIG_FRAMEBUFFER_CONSOLE_DEFERRED_TAKEOVER=n \
    CONFIG_VT_HW_CONSOLE_BINDING=y \
    CONFIG_VT_CONSOLE_SLEEP=y \
    CONFIG_STAGING=y \
    CONFIG_FB_TFT=y \
    CONFIG_FB_TFT_ST7735S=y
  FILES:= \
    $(LINUX_DIR)/drivers/staging/fbtft/fbtft.ko \
    $(LINUX_DIR)/drivers/staging/fbtft/fb_st7735s.ko
  AUTOLOAD:=$(call AutoProbe,fbtft fb_st7735s)
endef

define KernelPackage/fbtft-gc9107/description
  ST7735S framebuffer driver (fbtft) for the MF68E MSM8916 display.
  Includes deferred I/O, sys_* helpers, PWM backlight and fbcon.
endef

define Build/Compile
endef

define KernelPackage/fbtft-gc9107/install
	$(INSTALL_DIR) $(1)/lib/preinit
	$(INSTALL_BIN) ./preinit/05_backlight_full $(1)/lib/preinit/05_backlight_full
endef

$(eval $(call KernelPackage,fbtft-gc9107))
