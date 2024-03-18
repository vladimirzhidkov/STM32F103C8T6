DEVICE = stm32f103c8t6
CPUCORE = ARM_CM3
PROJECT = blinky

SOURCE_DIR		= src
BUILD_DIR		= bin
OPENCM3_DIR		= ../../libopencm3
RTOS_DIR		= ../../FreeRTOSv202212.01

# relative to RTOS_DIR:
RTOS_KERNEL_DIR	= FreeRTOS/Source
RTOS_PORT_DIR	= $(RTOS_KERNEL_DIR)/portable/GCC/$(CPUCORE)

# my source files
CFILES := $(addprefix $(SOURCE_DIR)/, main.c opencm3.c)

# FreeRTOS source files
CFILES += $(addprefix $(RTOS_KERNEL_DIR)/,list.c tasks.c)
CFILES += $(RTOS_KERNEL_DIR)/portable/MemMang/heap_4.c
CFILES += $(RTOS_PORT_DIR)/port.c

INCLUDES := -Iinclude
INCLUDES += -I$(RTOS_DIR)/$(RTOS_KERNEL_DIR)/include
INCLUDES += -I$(RTOS_DIR)/$(RTOS_PORT_DIR)

# all is defined in ../rules.mk
start: all

# special rule to keep freeRTOS object files inside bin/
$(BUILD_DIR)/%.o: $(RTOS_DIR)/%.c
	@printf "  CC\t$<\n"
	@mkdir -p $(dir $@)
	$(Q)$(CC) $(TGT_CFLAGS) $(CFLAGS) $(TGT_CPPFLAGS) $(CPPFLAGS) -o $@ -c $<

flash: $(PROJECT).bin 
	st-flash write $< 0x08000000

#OOCD_FILE = board/stm32f4discovery.cfg

# You shouldn't have to edit anything below here.
#VPATH += $(SHARED_DIR)

include $(OPENCM3_DIR)/mk/genlink-config.mk
include ../../rules.mk
include $(OPENCM3_DIR)/mk/genlink-rules.mk