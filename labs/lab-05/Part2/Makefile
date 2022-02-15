vpath %.h headers
vpath %.c source

all: static_block dynamic_block

static_block: program.o libblock.a
	cc program.o libblock.a -o static_block -Wl,-rpath .

dynamic_block: program.o libblock.so
	cc program.o libblock.so -o dynamic_block -Wl,-rpath .

program.o: program.c
	cc -c $< -o $@

libblock.so: block.o
	cc -shared -o libblock.so block.o

libblock.a: block.o
	ar qc libblock.a block.o

block.o: block.c
	cc -fPIC -c $< -o $@

block.o: block.h

clean:
	rm -f dynamic_block static_block *.a *.so *.o all