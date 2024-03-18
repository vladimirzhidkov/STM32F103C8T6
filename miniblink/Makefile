PROJECT = miniblink
BUILD_DIR = bin
SOURCE_DIR = src

#SHARED_DIR = ../my-common-code
CFILES := $(addprefix $(SOURCE_DIR)/, main.c)
#CFILES += api.c
#AFILES += api-asm.S

# TODO - you will need to edit these two lines!

DEVICE=stm32f103c8t6
start: all
send: $(PROJECT).bin 
	st-flash write $(PROJECT).bin 0x08000000

#OOCD_FILE = board/stm32f4discovery.cfg

# You shouldn't have to edit anything below here.
VPATH += $(SHARED_DIR)
INCLUDES += $(patsubst %,-I%, . $(SHARED_DIR))
OPENCM3_DIR=../libopencm3

include $(OPENCM3_DIR)/mk/genlink-config.mk
include ../rules.mk
include $(OPENCM3_DIR)/mk/genlink-rules.mk
