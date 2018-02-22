# Makefile
#
CC=g++ -O2 -std=c++11
LIBS=-lfst -ldl -lm
OUT=phonetisaurus-g2p
TMP=*.o
EXTRA=-L/usr/local/Cellar/openfst/1.5.0/lib/ -I/usr/local/Cellar/openfst/1.5.0/include

OBJS=Phonetisaurus.o FstPathFinder.o

all: phonetisaurus-g2p

Phonetisaurus.o: Phonetisaurus.cpp
	$(CC) $(EXTRA) Phonetisaurus.cpp -c -o Phonetisaurus.o

FstPathFinder.o: FstPathFinder.cpp
	$(CC) $(EXTRA) FstPathFinder.cpp -c -o FstPathFinder.o

phonetisaurus-g2p: FstPathFinder.o Phonetisaurus.o phonetisaurus-g2p.cpp
	$(CC) $(EXTRA) $(OBJS) phonetisaurus-g2p.cpp -o phonetisaurus-g2p $(LIBS)

clean:
	rm $(OUT) $(TMP) 
