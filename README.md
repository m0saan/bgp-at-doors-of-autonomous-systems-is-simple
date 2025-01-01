# bgp-at-doors-of-autonomous-systems-is-simple


# First check if there are any running containers
docker ps

# Remove Docker packages (using the correct package names for Ubuntu 22.04)
sudo apt-get purge -y docker.io docker-compose containerd.io
sudo apt-get autoremove -y --purge docker.io docker-compose

# Remove Docker directories and files
sudo rm -rf /var/lib/docker
sudo rm -rf /etc/docker
sudo rm -rf ~/.docker
sudo rm -rf /var/run/docker.sock

# Clean up
sudo apt-get autoremove -y
sudo apt-get clean


# Remove GNS3 packages
sudo apt purge -y gns3-gui gns3-server

# Remove dependencies that are no longer needed
sudo apt autoremove -y

# Remove GNS3 configuration files
rm -rf ~/.config/GNS3
rm -rf ~/.local/share/GNS3

# Remove the GNS3 PPA
sudo add-apt-repository --remove ppa:gns3/ppa

# Update package list
sudo apt update


docker-install:
	@echo "Installing Docker..."
	sudo apt install -y docker.io
	@echo "Docker installation completed"

docker-config:
	@echo "Configuring Docker..."
	sudo systemctl start docker &&\
	sudo systemctl enable docker &&\
	sudo usermod -aG docker gns3 &&\
	sleep 3 &&\
	sudo systemctl restart docker &&\
	sleep 2 &&\
	newgrp docker
	@echo "Docker configuration completed"