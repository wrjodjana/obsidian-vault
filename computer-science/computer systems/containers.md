### Vocabulary

**Image:** a particular container setup, usually Linux OS with a set of preinstalled programs and files. Captures the state that each container should have when first set up.

**Container:** an isolated lightweight virtual machine. When first created, has a state that perfectly matches some image, thereafter programs that run in the container can change that state in the way that programs do, adding and removing files

**Runtime:** program that makes containers, loads images onto them and runs them

### Creating Images

**Dockerfile:**
- `FROM imagename` initializes an image by copying another image