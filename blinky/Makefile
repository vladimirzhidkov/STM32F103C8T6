PROJECT = blinky
BUILD_DIR = bin

SHARED_DIR = #../my-common-code
CFILES = main.c opencm3.c
#CFILES += api.c
#AFILES += api-asm.S

# my adds - start
#RTOS_SOURCE_DIR = rtos
#RTOS_SOURCE += heap_4.c list.c port.c tasks.c opencm3.c 
RTOS = ../FreeRTOSv202212.01
RTOS_SOURCE_DIR = $(RTOS)/FreeRTOS/Source
RTOS_PORT_DIR = $(RTOS_SOURCE_DIR)/portable/GCC/ARM_CM3
RTOS_MEM_MANG_DIR = $(RTOS_SOURCE_DIR)/portable/MemMang

CFILES += $(addprefix $(RTOS_SOURCE_DIR)/,list.c tasks.c queue.c)
CFILES += $(addprefix $(RTOS_MEM_MANG_DIR)/,heap_4.c)
CFILES += $(RTOS_PORT_DIR)/port.c

INCLUDES += -I$(RTOS_SOURCE_DIR)/include
INCLUDES += -I$(RTOS_PORT_DIR)
INCLUDES += -I.

#$(info cfiles: $(CFILES))
#$(info includes: $(INCLUDES))

V = 1	# verbosity control variable (used in ../rules.mk)
# my adds - end 

# TODO - you will need to edit these two lines!
DEVICE=stm32f103c8t6
OOCD_FILE = #board/stm32f4discovery.cfg

# You shouldn't have to edit anything below here.
VPATH += $(SHARED_DIR)
INCLUDES += $(patsubst %,-I%, . $(SHARED_DIR))
OPENCM3_DIR=../libopencm3

include $(OPENCM3_DIR)/mk/genlink-config.mk
include ../rules.mk
include $(OPENCM3_DIR)/mk/genlink-rules.mk
