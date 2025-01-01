# Makefile to (re)build and clean docker images

all: gns3-install build

gns3-install:
	@echo "Installing GNS3..."
	sudo add-apt-repository -y ppa:gns3/ppa
	sudo apt update
	sudo apt install -y gns3-gui gns3-server
	@echo "GNS3 installation completed"

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
