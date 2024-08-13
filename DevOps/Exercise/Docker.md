# Create a Docker Container

## Setup 
1) On AWS, Go to your instance, then Security and then Security Group. Edit the inbound rules , to check or allow ports 8080 and 80. Select *Anywhere IPv4* for source.
2) Install Docker on the EC2 instance and start the docker daemon. Use the following [commands](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04):
- `sudo apt-get update`
- `sudo apt install apt-transport-https ca-certificates curl software-properties-common`
- `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
- `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"`
- `apt-cache policy docker-ce`
- `sudo apt install docker-ce`

Then use `sudo systemctl status docker` to confrim that it has been installed and active on the instance. if it's not running , try `sudo service docker start` to start it .

## Test Site
Go into the test-site folder
- `cd test-site`
Create a dockerfile with httpd content
- `vim dockerfile`
- `FROM httpd:2.4`: type this into the dockerfile.
Build the dockerfile into an image.
- `sudo docker build -t test-httpd .`
Use the command to check if the image was build.
- `sudo docker images`
Deploy the image to a container.
- `sudo docker run -dit test-httpd`
To check the docker is running correctly
- `curl 127.0.0.1:80`

## Dev Site