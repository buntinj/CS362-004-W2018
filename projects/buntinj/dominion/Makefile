CFLAGS = -Wall -fpic -coverage -lm

rngs.o: rngs.h rngs.c
	gcc -c rngs.c -g  $(CFLAGS)

dominion.o: dominion.h dominion.c rngs.o
	gcc -c dominion.c -g  $(CFLAGS)

playdom: dominion.o playdom.c
	gcc -o playdom playdom.c -g dominion.o rngs.o $(CFLAGS)
#To run playdom you need to entere: ./playdom <any integer number> like ./playdom 10*/
testDrawCard: testDrawCard.c dominion.o rngs.o
	gcc  -o testDrawCard -g  testDrawCard.c dominion.o rngs.o $(CFLAGS)

badTestDrawCard: badTestDrawCard.c dominion.o rngs.o
	gcc -o badTestDrawCard -g  badTestDrawCard.c dominion.o rngs.o $(CFLAGS)

testBuyCard: testDrawCard.c dominion.o rngs.o
	gcc -o testBuyCard -g  testDrawCard.c dominion.o rngs.o $(CFLAGS)

testAll: dominion.o testSuite.c
	gcc -o testSuite testSuite.c -g  dominion.o rngs.o $(CFLAGS)

interface.o: interface.h interface.c
	gcc -c interface.c -g  $(CFLAGS)

runtests: testDrawCard 
	./testDrawCard &> unittestresult.out
	gcov dominion.c >> unittestresult.out
	cat dominion.c.gcov >> unittestresult.out


player: player.c interface.o
	gcc -o player player.c -g  dominion.o rngs.o interface.o $(CFLAGS)

testUpdateCoins: testUpdateCoins.c dominion.o rngs.o
	gcc -o testUpdateCoins -g testUpdateCoins.c dominion.o rngs.o $(CFLAGS)

unittest1: unittest1.c dominion.o rngs.o
	gcc -o unittest1 -g unittest1.c dominion.o rngs.o $(CFLAGS)

unittest2: unittest2.c dominion.o rngs.o
	gcc -o unittest2 -g unittest2.c dominion.o rngs.o $(CFLAGS)

unittest3: unittest3.c dominion.o rngs.o
	gcc -o unittest3 -g unittest3.c dominion.o rngs.o $(CFLAGS)

unittest4: unittest4.c dominion.o rngs.o
	gcc -o unittest4 -g unittest4.c dominion.o rngs.o $(CFLAGS)

cardtest1: cardtest1.c dominion.o rngs.o
	gcc -o cardtest1 -g cardtest1.c dominion.o rngs.o $(CFLAGS)

cardtest2: cardtest2.c dominion.o rngs.o
	gcc -o cardtest2 -g cardtest2.c dominion.o rngs.o $(CFLAGS)

cardtest3: cardtest3.c dominion.o rngs.o
	gcc -o cardtest3 -g cardtest3.c dominion.o rngs.o $(CFLAGS)

cardtest4: cardtest4.c dominion.o rngs.o
	gcc -o cardtest4 -g cardtest4.c dominion.o rngs.o $(CFLAGS)

unittestresults.out: dominion.o rngs.o unittest1 unittest2 unittest3 unittest4 cardtest1 cardtest2 cardtest3 cardtest4
	./unittest1 &> unittestresults.out
	echo "supplyCard stats" >> unittestresults.out
	gcov -abcfu  dominion.c | sed -n '/supplyCount/{n;p; n;p; n;p; n;p}' >> unittestresults.out
	./unittest2 >> unittestresults.out
	echo "numHandCards stats" >> unittestresults.out
	gcov -abcfu dominion.c | sed -n '/numHandCards/{n;p; n;p; n;p; n;p}' >> unittestresults.out
	./unittest3 >> unittestresults.out
	echo "getCost stats" >> unittestresults.out
	gcov -abcfu dominion.c | sed -n '/getCost/{n;p; n;p; n;p; n;p}' >> unittestresults.out
	./unittest4 >> unittestresults.out
	echo "isGameOver stats" >> unittestresults.out
	gcov -abcfu dominion.c | sed -n '/isGameOver/{n;p; n;p; n;p; n;p}' >> unittestresults.out
	./cardtest1 >> unittestresults.out
	echo "cardEffect stats" >> unittestresults.out
	gcov -abcfu dominion .c | sed -n '/cardEffect/{n;p; n;p; n;p; n;p;}' >> unittestresults.out
	./cardtest2 >> unittestresults.out
	echo "cardEffect stats" >> unittestresults.out
	gcov -abcfu dominion .c | sed -n '/cardEffect/{n;p; n;p; n;p; n;p;}' >> unittestresults.out
	./cardtest3 >> unittestresults.out
	echo "cardEffect stats" >> unittestresults.out
	gcov -abcfu dominion .c | sed -n '/cardEffect/{n;p; n;p; n;p; n;p;}' >> unittestresults.out
	./cardtest4 >> unittestresults.out
	echo "cardEffect stats" >> unittestresults.out
	gcov -abcfu dominion .c | sed -n '/cardEffect/{n;p; n;p; n;p; n;p;}' >> unittestresults.out

randomtestcard1.out: randomtestcard1.c dominion.o rngs.o
	gcc -o randomtestcard1 -g randomtestcard1.c dominion.o rngs.o $(CFLAGS)
	./randomtestcard1 &> randomtestcard1.out
	echo "cardEffect stats" >> randomtestcard1.out
	gcov -abcfu dominion.c | sed -n '/cardEffect/{n;p; n;p; n;p; n;p}' >> randomtestcard1.out

randomtestcard2.out: randomtestcard2.c dominion.o rngs.o
	gcc -o randomtestcard2 -g randomtestcard2.c dominion.o rngs.o $(CFLAGS)
	./randomtestcard2 &> randomtestcard2.out
	echo "cardEffect stats" >> randomtestcard2.out
	gcov -abcfu dominion.c | sed -n '/cardEffect/{n;p; n;p; n;p; n;p}' >> randomtestcard2.out

randomtestadventurer.out: randomtestadventurer.c dominion.o rngs.o
	gcc -o randomtestadventurer -g randomtestadventurer.c dominion.o rngs.o $(CFLAGS)
	./randomtestadventurer &> randomtestadventurer.out
	echo "Adventurer stats" >> randomtestadventurer.out
	gcov -abcfu dominion.c | sed -n '/Adventurer/{n;p; n;p; n;p; n;p}' >> randomtestadventurer.out

all: playdom player testDrawCard testBuyCard badTestDrawCard

clean:
	rm -f *.o playdom.exe playdom player player.exe  *.gcov *.gcda *.gcno *.so *.out testDrawCard testDrawCard.exe
