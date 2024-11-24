.SILENT:

NUM_PT=500

all: aes hamming
	chmod +x generate_key.sh

lib:
	make -C ../measure/

aes: lib aes.cpp
	g++ -DNUM_PT=${NUM_PT} -maes aes.cpp -L../measure -I../measure -l:libmeasure.a -o aes

hamming: hamming.cpp
	# g++ -DNUM_PT=${NUM_PT} -mssse3 -maes hamming.cpp -o hamming
	g++ -std=c++17 -march=armv8-a+fp+simd+crypto+crc hamming.cpp -o hamming

run: hamming
	./generate_key.sh ${NUM_PT}

clean:
	make -C ../measure/ clean
	rm hamming aes