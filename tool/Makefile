all: tlstunnel testcli testsrv

clean:
	rm -f *.o testcli testsrv tlstunnel

.c.o:
	gcc -ggdb3 -pthread -fPIC -I ../include -I /usr/local/include -c -o $@ $<

../lib/libstarttls.so:
	make -C ../lib libstarttls.so

../lib/libstarttls.a:
	make -C ../lib libstarttls.a

tlstunnel: tlstunnel.o ../lib/libstarttls.so
	gcc -pthread -I ../include -o $@ tlstunnel.o ../lib/libstarttls.so

testcli: testcli.o ../lib/libstarttls.a
	gcc -o $@ testcli.o ../lib/libstarttls.a

testsrv: testsrv.o ../lib/libstarttls.a
	gcc -o $@ testsrv.o ../lib/libstarttls.a
