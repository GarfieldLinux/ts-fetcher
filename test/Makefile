.SUFFIXES: .cc .o .lo

COMPILE = $(CXX) -Wall -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -g
INC_PATH = -Imodules
LIB_PATH = -L/usr/local/lib -ltsfetcher

SHARED_OBJS = test_post.lo test1.lo
ALL_OBJS = $(SHARED_OBJS)

ALL_PRGS = 
ALL_LIBS = libtest1.so libtest_post.so

all: $(ALL_OBJS) $(ALL_PRGS) $(ALL_LIBS)

libtest_post.so:
	$(COMPILE) -o $@ $< -shared test_post.lo $(LIB_PATH)
libtest1.so:
	$(COMPILE) -o $@ $< -shared test1.lo $(LIB_PATH)
.cc:
	$(COMPILE) -o $@ $< $(SHARED_OBJS) $(LIB_PATH) $(INC_PATH)
.cc.o:
	$(COMPILE) -c -o $@ $<  $(INC_PATH)
.cc.lo:
	$(COMPILE) -c -fPIC -o $@ $<  $(INC_PATH)
install:
	/bin/cp -f $(ALL_LIBS) /usr/lib64/
clean:
	rm -f $(ALL_OBJS) $(ALL_PRGS) $(ALL_LIBS)

