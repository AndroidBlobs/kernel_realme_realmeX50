# SPDX-License-Identifier: GPL-2.0
#ifndef VENDOR_EDIT
#/*Fei.Mo@BSP.kernel.Stability, 2019/07/11, Add for spllit dtbo*/
#subdir-y += actions
#subdir-y += al
#subdir-y += allwinner
#subdir-y += altera
#subdir-y += amd
#subdir-y += amlogic
#subdir-y += apm
#subdir-y += arm
#subdir-y += broadcom
#subdir-y += cavium
#subdir-y += exynos
#subdir-y += freescale
#subdir-y += hisilicon
#subdir-y += lg
#subdir-y += marvell
#subdir-y += mediatek
#subdir-y += nvidia
#subdir-y += qcom
#subdir-y += realtek
#subdir-y += renesas
#subdir-y += rockchip
#subdir-y += socionext
#subdir-y += sprd
#subdir-y += synaptics
#subdir-y += ti
#subdir-y += xilinx
#subdir-y += zte
#else
subdir-y += qcom
#endif
subdir-y += 20620

dtstree		:= $(srctree)/$(src)

vendor := $(dtstree)/vendor
ifneq "$(wildcard $(vendor)/Makefile)" ""
        subdir-y += vendor
endif

dtb-$(CONFIG_OF_ALL_DTBS) := $(patsubst $(dtstree)/%.dts,%.dtb, $(foreach d,$(subdir), $(wildcard $(dtstree)/$(d)/*.dts)))

always		:= $(dtb-y)

targets += dtbs

DTB_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM64_APPENDED_DTB_IMAGE_NAMES))
ifneq ($(DTB_NAMES),)
DTB_LIST := $(addsuffix .dtb,$(DTB_NAMES))
else
DTB_LIST := $(dtb-y)
endif
targets += $(DTB_LIST)

dtbs: $(addprefix $(obj)/, $(DTB_LIST))

clean-files := dts/*.dtb *.dtb
