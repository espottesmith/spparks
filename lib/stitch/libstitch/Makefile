# mpicc and mpicxx must be on your path; Set these appropriately

CC=mpicc
CXX=mpicxx
TARGET_DIR=${HOME}/local/stitch

stitch.lib: stitch.c stitch.h sqlite3.c sqlite3.h
	CC="${CC}" CXX="${CXX}" ${CC} -std=gnu99 -c stitch.c sqlite3.c -DSTITCH_PARALLEL -lstitch -ldl -lpthread
	ar rc libstitch.a stitch.o sqlite3.o

stitch_module: stitch.c stitch.h sqlite3.c sqlite3.h
	cd .. ; CC="gcc" CXX="g++" python3 setup.py build && CC="gcc" CXX="g++" python3 setup.py install

clean:
	cd .. ; python3 setup.py clean
	rm -f *.o libstitch.a *.so 
	rm -rf ${TARGET_DIR}
	rm -rf ../build
	find .. -name __pycache__ -exec rm -rf {} \; ; find .. -name "*.pyc" -exec rm -rf {} \; ; rm -f *.st
