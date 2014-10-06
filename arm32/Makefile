CFG_TEE_CORE_CORE_TARGET := armv7

#########################################################################
# Set Internal Variables                                                #
# May be modified to match your setup                                   #
#########################################################################
CFG_TEE_DRV_DEBUGFS?=0
CFG_TEE_CORE_LOG_LEVEL?=2
CFG_TEE_TA_LOG_LEVEL?=2

ccflags-y+=-Werror
ccflags-y+=-I$(BUILD_DIR_TEE_DRV)/include/arm_common
ccflags-y+=-I$(BUILD_DIR_TEE_DRV)/include/linux
ccflags-y+=-I$(BUILD_DIR_TEE_DRV)/include
ccflags-y+=-I$(BUILD_DIR_TEE_DRV)/core

ccflags-y+=-DCFG_TEE_DRV_DEBUGFS=${CFG_TEE_DRV_DEBUGFS}
ccflags-y+=-DCFG_TEE_CORE_LOG_LEVEL=${CFG_TEE_CORE_LOG_LEVEL}
ccflags-y+=-DCFG_TEE_TA_LOG_LEVEL=${CFG_TEE_TA_LOG_LEVEL}

# "smc" assembly intruction requires dedicated "armv7 secure extension"
secext := $(call as-instr,.arch_extension sec,+sec)
AFLAGS_stm-smc.o := -Wa,-march=armv7-a$(secext)

obj-m += optee_arm32.o

optee_arm32-objs:=   \
		tee_tz_drv.o \
		tee_mem.o \
		stm-smc.o \
		handle.o


