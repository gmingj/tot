CC=$(CROSS_COMPILE)gcc

BIN=a.out
SRC_PATH=. #src
OBJ_PATH=obj
IFLAGS= #-I./include
CFLAGS=-c -Wall #-Werror
LFLAGS=

SOURCES=$(foreach dir, $(SRC_PATH), $(wildcard $(dir)/*.c))
OBJS=$(addprefix $(OBJ_PATH)/, $(patsubst %.c, %.o, $(notdir $(SOURCES))))
VPATH=$(SRC_PATH) #$(LIB_SRC_PATH)

ifeq ($(DBG), y)
	CFLAGS+=-g -DDEBUG
endif

all:$(BIN)

$(BIN): $(OBJS) #$(LIB_TARGET)
	$(CC) $^ $(LFLAGS) -o $@

$(OBJ_PATH)/%.o:%.c
	@if [ ! -d $(OBJ_PATH) ]; then mkdir -p $(OBJ_PATH); fi;
	$(CC) $(CFLAGS) $< $(IFLAGS) -o $@

.PHONY:clean
clean:
	@if [ -d $(OBJ_PATH) ]; then rm -rf $(OBJ_PATH); fi
	@if [ -f $(LIB_TARGET) ]; then rm -rf $(LIB_TARGET); fi
	@if [ -f $(BIN) ]; then rm -rf $(BIN); fi
