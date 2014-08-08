# lifted from the teensyduino makefile
TARGET = main

MCU=mk20dx128
CPU=cortex-m4
# configurable options
OPTIONS = -DF_CPU=48000000 -DUSB_SERIAL -DLAYOUT_US_ENGLISH

# options needed by many Arduino libraries to configure for Teensy 3.0
#OPTIONS += -D__MK20DX128__ -DARDUIO=105 -DTEENSYDUINO=118


CPPFLAGS = -Wall -g -Os -mcpu=$(CPU) -mthumb -nostdlib -MMD $(OPTIONS) -I.
CXXFLAGS = -std=gnu++0x -felide-constructors -fno-exceptions -fno-rtti
CFLAGS =
LDFLAGS = -Os -Wl,--gc-sections -mcpu=$(CPU) -mthumb -Tmk20dx128.ld
LIBS = -lm

CC = arm-none-eabi-gcc
CXX = arm-none-eabi-g++
OBJCOPY = arm-none-eabi-objcopy
SIZE = arm-none-eabi-size
TEENSY_LOADER_CLI = ~/Development/teensy_loader_cli/teensy_loader_cli



# Other Makefiles and project templates for Teensy 3.x:
#
# https://github.com/apmorton/teensy-template
# https://github.com/xxxajk/Arduino_Makefile_master
# https://github.com/JonHylands/uCee



# automatically create lists of the sources and objects
C_FILES := $(wildcard *.c)
CPP_FILES := $(wildcard *.cpp)
OBJS := $(C_FILES:.c=.o) $(CPP_FILES:.cpp=.o)


all: $(TARGET).hex

$(TARGET).elf: $(OBJS) mk20dx128.ld
	$(CC) $(LDFLAGS) -o $@ $(OBJS) $(LIBS)

# from teensyduino
#TOOLSPATH = $(ARDUINOPATH)/hardware/tools   # on Linux
#%.hex: %.elf
#	$(SIZE) $<
#	$(OBJCOPY) -O ihex -R .eeprom $< $@
#	$(abspath $(TOOLSPATH))/teensy_post_compile -file=$(basename $@) -path=$(shell pwd) -tools=$(abspath $(TOOLSPATH))
#	-$(abspath $(TOOLSPATH))/teensy_reboot

# from teensy website
# Create final output files (.hex, .eep) from ELF output file.
%.hex: %.elf
        @echo
        @echo $(MSG_FLASH) $@
        $(OBJCOPY) -O $(FORMAT) -R .eeprom -R .fuse -R .lock -R .signature $< $@
        $(TEENSY_LOADER_CLI) -mmcu=$(MCU) -w -v $@


# compiler generated dependency info
-include $(OBJS:.o=.d)

clean:
	rm -f *.o *.d $(TARGET).elf $(TARGET).hex
