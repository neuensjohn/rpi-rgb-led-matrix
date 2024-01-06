# Creating RGB matrix library
# When you link this library with your binary, you need to add -lrt -lm -lpthread
# So
#   -lrgbmatrix
##
OBJECTS=gpio.o led-matrix.o options-initialize.o framebuffer.o \
        thread.o bdf-font.o graphics.o led-matrix-c.o hardware-mapping.o \
        pixel-mapper.o multiplex-mappers.o \
	content-streamer.o

TARGET=librgbmatrix

INCDIR=../include
CFLAGS=-W -Wall -Wextra -Wno-unused-parameter -O3 -g -fPIC $(DEFINES)
CXXFLAGS=$(CFLAGS) -fno-exceptions -std=c++11

all : $(TARGET).a $(TARGET).so.1

$(TARGET).a : $(OBJECTS)
	$(AR) rcs $@ $^

$(TARGET).so.1 : $(OBJECTS)
	$(CXX) -shared -Wl,-soname,$@ -o $@ $^ -lpthread  -lrt -lm -lpthread

led-matrix.o: led-matrix.cc $(INCDIR)/led-matrix.h
thread.o : thread.cc $(INCDIR)/thread.h
framebuffer.o: framebuffer.cc framebuffer-internal.h
graphics.o: graphics.cc utf8-internal.h

%.o : %.cc compiler-flags
	$(CXX) -I$(INCDIR) $(CXXFLAGS) -c -o $@ $<

%.o : %.c compiler-flags
	$(CC)  -I$(INCDIR) $(CFLAGS) -c -o $@ $<

clean:
	rm -f $(OBJECTS) $(TARGET).a $(TARGET).so.1

compiler-flags: FORCE
	@echo '$(CXX) $(CXXFLAGS)' | cmp -s - $@ || echo '$(CXX) $(CXXFLAGS)' > $@

.PHONY: FORCE
