###########################################################
# Makefile
#
# History:
# 2013-06-05 Dennis Create
###########################################################

CC= gcc

INC=-I./
SRC := $(shell find ./ -name '*.c')
OBJS := $(SRC:.c=.o)

all: $(OBJS)

$(OBJS): %.o:%.c
	$(CC) -c $< ${INC}

.PHONY: clean
clean:
	rm -f *.o 
