# Makefile to (re)build and clean docker images

all: build

build:
	docker build --file=mamali_host-1 --tag=mamali_host .
	echo "Alpine image is built"\

	docker build --file=mamali_router-1 --tag=mamali_router .
	echo "Router image is build"

clean:
	yes | docker image prune -a
vs : 
	docker images

re: clean all

.PHONY: all build clean re
