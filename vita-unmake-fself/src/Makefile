TARGET = vita-unmake-fself

OBJS = main.o

LIBS = -lz 

CFLAGS = -Wall -Wextra -std=c99

UNAME_S := $(shell uname -s)
ifneq ($(UNAME_S),Darwin)
CFLAGS += -s -static
LDFLAGS += -static -static-libgcc
endif

.PHONY: all clean mrproper install

all: $(TARGET)

$(TARGET): $(OBJS)
	@echo "Creating binary $(TARGET)"
	$(CXX) $(LDFLAGS) $(OBJS) -o $@ $(LIBS)

%.o: %.c
	@echo "Compiling $^"
	$(CC) $(CPPFLAGS) $(CFLAGS) -c $< -o $@

clean:
	@echo "Removing all the .o files"
	@$(RM) $(OBJS)

mrproper: clean
	@echo "Removing binary"
	@$(RM) $(TARGET)

install: all
	@cp $(TARGET) ../bin
