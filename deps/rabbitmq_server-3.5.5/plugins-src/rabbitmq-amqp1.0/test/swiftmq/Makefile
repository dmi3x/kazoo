CLIENT_DIR=swiftmq_9_7_1_client
CLIENT_PKG=$(CLIENT_DIR).tar.gz

.PHONY: test

test: build/lib
	ant test

build/lib: $(CLIENT_PKG)
	mkdir -p build/tmp
	tar -zx -f $(CLIENT_PKG) -C build/tmp
	mkdir -p build/lib
	mv build/tmp/$(CLIENT_DIR)/jars/*.jar build/lib
	rm -rf build/tmp
	cp ../lib-java/*.jar build/lib
	(cd ../../../rabbitmq-java-client && ant dist)
	cp ../../../rabbitmq-java-client/build/dist/rabbitmq-client.jar build/lib

$(CLIENT_PKG):
	@echo
	@echo You need $(CLIENT_PKG) to run these tests. Unfortunately we can\'t
	@echo redistribute it. Obtain it from the SwiftMQ website and place it
	@echo in $(shell pwd).
	@echo
	@false

clean:
	rm -rf build
