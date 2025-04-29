### Vocabulary

**Image:** a particular container setup, usually Linux OS with a set of preinstalled programs and files. Captures the state that each container should have when first set up.

**Container:** an isolated lightweight virtual machine. When first created, has a state that perfectly matches some image, thereafter programs that run in the container can change that state in the way that programs do, adding and removing files

**Runtime:** program that makes containers, loads images onto them and runs them

### Creating Images

**Dockerfile:**
- `FROM imagename` initializes an image by copying another image
	- Starting from pre-built image makes writing Dockerfile easy
	- `FROM scratch` copies nothing
- `RUN shell command` runs command inside the image during setup
	- Runs installation commands from a package manager from the `FROM` command
	- Dockerfile RUN vs `docker run`
		- Since RUN is inside a Dockerfile, it runs while setting up the image, changes it makes t