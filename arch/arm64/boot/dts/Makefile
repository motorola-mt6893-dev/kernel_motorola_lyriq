# SPDX-License-Identifier: GPL-2.0
subdir-y += actions
subdir-y += al
subdir-y += allwinner
subdir-y += altera
subdir-y += amd
subdir-y += amlogic
subdir-y += apm
subdir-y += arm
subdir-y += broadcom
subdir-y += cavium
subdir-y += exynos
subdir-y += freescale
subdir-y += hisilicon
subdir-y += lg
subdir-y += marvell
subdir-y += mediatek
subdir-y += nvidia
subdir-y += qcom
subdir-y += realtek
subdir-y += renesas
subdir-y += rockchip
subdir-y += socionext
subdir-y += sprd
subdir-y += synaptics
subdir-y += ti
subdir-y += xilinx
subdir-y += zte


dtstree		:= $(srctree)/$(src)

dtb-$(CONFIG_OF_ALL_DTBS) := $(patsubst $(dtstree)/%.dts,%.dtb, $(foreach d,$(subdir), $(wildcard $(dtstree)/$(d)/*.dts)))

always		:= $(dtb-y)

targets += dtbs

DTB_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM64_APPENDED_DTB_IMAGE_NAMES))
ifneq ($(DTB_NAMES),)
DTB_LIST := $(addsuffix .dtb,$(DTB_NAMES))
else
DTB_LIST := $(dtb-y)
endif

DTBO_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM64_DT_OVERLAY_IMAGE_NAMES))
ifneq ($(DTBO_NAMES),)
DTB_LIST += $(addsuffix .dtbo,$(DTBO_NAMES))
endif

targets += $(DTB_LIST)

ifeq ($(strip $(CONFIG_BUILD_ARM64_DT_OVERLAY)), y)
dtbo-y += $(addsuffix .dtbo, $(subst $\",,$(CONFIG_BUILD_ARM64_DT_OVERLAY_IMAGE_NAMES)))
endif

dtbs: $(addprefix $(obj)/, $(DTB_LIST))

clean-files := dts/*.dtb *.dtb *.dtbo
