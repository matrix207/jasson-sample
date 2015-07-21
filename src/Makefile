###########################################################
# Makefile
# 
# History:
#    v1.0  2014-06-19 Dennis  Create
###########################################################
.SUFFIXES : .x .o .c .cpp .s
ROOTDIR	= $(shell pwd)

CC     = gcc
CFLAGS+= -Wall -g
INCPATH = $(ROOTDIR)
INCPRG  =-I$(INCPATH) \
         -I$(INCPATH)/jansson
		
INCDIR  = $(INCPRG)

CFLAGS += $(INCDIR)

#SOURCES:=$(shell find $(ROOTDIR) -name '*.cpp' -o -name '*.c')
SOURCES:=$(shell find $(ROOTDIR) -maxdepth 1 -name '*.cpp' -o -name '*.c')
CPPSRC :=$(notdir $(SOURCES))
OBJECTS:=$(CPPSRC:.c=.o)

# search all subdirs
#subdirs := $(sort $(subst /,,$(dir $(wildcard */*))))
subdirs := ./jansson/

# generate subdirs object name
OBJS_OTHER_SRC := $(shell find $(subdirs) -name '*.c')
OBJS_OTHER := $(OBJS_OTHER_SRC:.c=.o)

TARGET = test

all: $(TARGET)

$(TARGET): $(OBJECTS)
	@echo "**************** build subdir ****************"
	$(foreach N,$(subdirs),make -C $(N);)
	@echo "**************** link target ****************"
	$(CC) -o $(TARGET) $(OBJECTS) $(OBJS_OTHER) $(SHARLIB) $(CFLAGS)

$(OBJECTS): %.o:%.c
	$(CC) -c $< $(CFLAGS)

.PHONY: clean
clean:
	$(foreach N,$(subdirs),make -C $(N) clean;)
	rm -f *.o $(TARGET) 

