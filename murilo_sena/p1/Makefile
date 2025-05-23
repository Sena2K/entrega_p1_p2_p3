CC = gcc
CFLAGS = -Wall -O2

all: compilador assembler executor

compilador: compilador.c neander.h
	$(CC) $(CFLAGS) -o compilador compilador.c

assembler: assembler.c neander.h
	$(CC) $(CFLAGS) -o assembler assembler.c

executor: executor.c neander.h
	$(CC) $(CFLAGS) -o executor executor.c

clean:
	rm -f compilador assembler executor programa.asm programa.bin
