### Vocabulary

**Image:** a particular container setup, usually Linux OS with a set of preinstalled programs and files. Captures the state that each container should have when first set up.

**Container:** an isolated lightweight virtual machine. When first created, has a state that perfectly matches some image, thereafter programs that run in the container can change that state in the way that programs do, adding and removing files

**Runtime:** program that makes containers, loads images onto them and runs them

### Creating Images

**Dockerfile:**
- `FROM [image name]` initializes an image by copying another image
	- Starting from pre-built image makes writing Dockerfile easy
	- `FROM scratch` copies nothing
- `RUN shell command` runs command inside the image during setup
	- Runs installation commands from a package manager from the `FROM` command
	- Dockerfile RUN vs `docker run`
		- Since RUN is inside a Dockerfile, it runs while setting up the image, changes it makes to the image persist and are copied into every container made from the image
		- `docker run` will only impact the state of the container only; image won't change
- `COPY local/path/inside/image` copies a file or directory tree from your computer into image
- `USER username` runs any commands that follow it and run in the image as the given user
- `WORKDIR /path/inside/image` basically `cd` in Dockerfile
- `CMD shell command` is a default command to run inside each container when it is started if no other command is provided
- To create image: `docker build -t myimagename`

### Listing and Deleting images

Image is stored internally with large hexadecimal ID
- `docker images` lists all images usable by containers
- `docker images --all` lists all images, even unnamed ones
- `docker rmi [image name]` removes a single image
- `docker image prune` removes all "dangling" images
- `docker system prune -all` both removes any stopped containers and any images that are not used by running containers

### Creating Containers

Creating new containers
- Specify the image using `docker run [image name]`
- `docker run` won't connect the container to any resources other than the CPU
- `-it` maps the container's stdin, stdout and stderr to the terminal
- `-p 5000:3456` causes network connections to port `5000` to be forwarded into the container and remapped to port `3456` inside it
- `-v /real/host/path:/inner/path` causes directory `/real/host/path` on your disk to show up in the container as `/inner/path`. Any changes the container makes to files in that path will be visible to you even after the container finishes.
- `--rm` tells the runtime to remove the container as soon as it is finished running

### Listing and deleting containers
- `docker container ls` lists the currently running containers
- `docker container ls -all` lists the currently exiting containers: both running and fi




