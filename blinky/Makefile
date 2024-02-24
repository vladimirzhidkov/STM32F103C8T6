# the full device name for generating ld script
DEVICE = stm32f103c8t6
CPUCORE = ARM_CM3

PROJECT = blinky

SOURCE_DIR		= src
BUILD_DIR		= bin
OPENCM3_DIR		= ../libopencm3
RTOS_DIR		= ../FreeRTOSv202212.01
# relative to RTOS_DIR:
RTOS_KERNEL_DIR	= FreeRTOS/Source
RTOS_PORT_DIR	= $(RTOS_KERNEL_DIR)/portable/GCC/$(CPUCORE)

CFILES := $(addprefix $(SOURCE_DIR)/, main.c opencm3.c)
CFILES += $(addprefix $(RTOS_KERNEL_DIR)/,list.c tasks.c)

# memory allocation scheme:
CFILES += $(RTOS_KERNEL_DIR)/portable/MemMang/heap_4.c
CFILES += $(RTOS_PORT_DIR)/port.c

INCLUDES := -I$(SOURCE_DIR)/include
INCLUDES += -I$(RTOS_DIR)/$(RTOS_KERNEL_DIR)/include
INCLUDES += -I$(RTOS_DIR)/$(RTOS_PORT_DIR)

# verbosity control variable (used in ../rules.mk)
# Be silent per default, but 'make V=1' will show all compiler calls.
# If you're insane, V=99 will print out all sorts of things.
V = 0

#OOCD_FILE = board/stm32f4discovery.cfg

# You shouldn't have to edit anything below here.
#VPATH += $(SHARED_DIR)

include $(OPENCM3_DIR)/mk/genlink-config.mk
include ../rules.mk
include $(OPENCM3_DIR)/mk/genlink-rules.mk