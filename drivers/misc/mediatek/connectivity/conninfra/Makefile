###############################################################################

#ifeq ($(CONFIG_MTK_COMBO_CHIP),)
#    $(error CONFIG_MTK_COMBO_CHIP not defined)
#endif

#ifeq ($(TARGET_BUILD_VARIANT),$(filter $(TARGET_BUILD_VARIANT),userdebug user))
#    ldflags-y += -s
#endif

# Force build fail on modpost warning
KBUILD_MODPOST_FAIL_ON_WARNINGS := y
###############################################################################

#ccflags-y += -D MTK_WCN_REMOVE_KERNEL_MODULE
ifeq ($(CONFIG_ARM64), y)
    ccflags-y += -D CONFIG_MTK_WCN_ARM64
endif

# Option for some ALPS specific feature, ex: AEE.
ccflags-y += -D CONNINFRA_PLAT_ALPS=1

#ifeq ($(CONFIG_MTK_CONN_LTE_IDC_SUPPORT),y)
#    ccflags-y += -D WMT_IDC_SUPPORT=1
#else
#    ccflags-y += -D WMT_IDC_SUPPORT=0
#endif

ccflags-y += -D MTK_WCN_WMT_STP_EXP_SYMBOL_ABSTRACT
ccflags-y += -D MTK_CONNINFRA_CLOCK_BUFFER_API_AVAILABLE=1

ccflags-y += -I$(srctree)/drivers/misc/mediatek/include
ccflags-y += -I$(srctree)/drivers/misc/mediatek/include/mt-plat/mt6885/include
ccflags-y += -I$(srctree)/drivers/misc/mediatek/include/mt-plat/mt6885/include/mach
ccflags-y += -I$(srctree)/drivers/misc/mediatek/include/mt-plat
ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/mt6885
ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include
ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include/clkbuf_v1
ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include/clkbuf_v1/mt6885
ccflags-y += -I$(srctree)/drivers/misc/mediatek/eccci
ccflags-y += -I$(srctree)/drivers/misc/mediatek/eccci/mt6885
ccflags-y += -I$(srctree)/drivers/misc/mediatek/eemcs
ccflags-y += -I$(srctree)/drivers/misc/mediatek/mach/mt6885/include/mach
ccflags-y += -I$(srctree)/drivers/misc/mediatek/emi/submodule
ccflags-y += -I$(srctree)/drivers/misc/mediatek/emi/mt6885
ccflags-y += -I$(srctree)/drivers/mmc/core
ccflags-y += -I$(srctree)/drivers/misc/mediatek/connectivity/common
ccflags-y += -I$(srctree)/drivers/misc/mediatek/pmic/include/
###############################################################################


ccflags-y += -Werror
ccflags-y += -Wno-error=format
ccflags-y += -Wno-error=format-extra-args

###############################################################################
MODULE_NAME := conninfra
$(warning $(MODULE_NAME) build-in boot.img)
obj-y += $(MODULE_NAME).o

###############################################################################
# common_main
###############################################################################
ccflags-y += -I$(src)/include
ccflags-y += -I$(src)/base/include
ccflags-y += -I$(src)/core/include
ccflags-y += -I$(src)/conf/include
ccflags-y += -I$(src)/platform/include
ccflags-y += -I$(src)/debug_utility
ccflags-y += -I$(src)/debug_utility/include
ccflags-y += -I$(src)/debug_utility/connsyslog
ccflags-y += -I$(src)/debug_utility/connsyslog/platform/include
ccflags-y += -I$(src)/debug_utility/coredump
ccflags-y += -I$(src)/debug_utility/coredump/platform/include
ccflags-y += -I$(src)/debug_utility/step/include

# By Plaftfrom
ccflags-y += -I$(src)/platform/mt6885/include

# Disable debugging
ccflags-y += -D CONNINFRA_DBG_SUPPORT=0

#ifeq ($(findstring evb, $(MTK_PROJECT)), evb)
#ccflags-y += -D CFG_WMT_EVB
#endif

#ifneq ($(filter "CONSYS_%",$(CONFIG_MTK_COMBO_CHIP)),)
#$(MODULE_NAME)-objs += common_main/platform/mt6885.o
#endif

$(MODULE_NAME)-objs += base/ring.o
#$(MODULE_NAME)-objs += base/osal.o
#$(MODULE_NAME)-objs += base/log.o
$(MODULE_NAME)-objs += base/msg_thread.o
$(MODULE_NAME)-objs += core/conninfra_core.o
$(MODULE_NAME)-objs += src/conninfra_dev.o
$(MODULE_NAME)-objs += src/conninfra.o
$(MODULE_NAME)-objs += conf/conninfra_conf.o
$(MODULE_NAME)-objs += platform/consys_hw.o
$(MODULE_NAME)-objs += platform/clock_mng.o
$(MODULE_NAME)-objs += platform/pmic_mng.o
$(MODULE_NAME)-objs += platform/emi_mng.o
$(MODULE_NAME)-objs += platform/consys_reg_mng.o

# By Plaftfrom
$(MODULE_NAME)-objs += platform/mt6885/mt6885.o
$(MODULE_NAME)-objs += platform/mt6885/mt6885_pmic.o
$(MODULE_NAME)-objs += platform/mt6885/mt6885_emi.o
$(MODULE_NAME)-objs += platform/mt6885/mt6885_consys_reg.o
$(MODULE_NAME)-objs += platform/mt6885/mt6885_pos.o
$(MODULE_NAME)-objs += platform/mt6885/mt6885.o
