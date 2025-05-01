
**coding**

rest api template
```Python
@routes.post("/") 
async def func(req : Request) -> Response:
	return Response()
```
- post could be replaced with put, get, delete
- response can have headers `status`, `text`
- status 200 usually means it's OK, while 500 means internal server error

reading request body
```Python
text = await req.text()
```
- to call the request body u use `await`
- `req.text()` is used to read the request body

reading `json` response
```Python
body = await req.json()
```
- use `.extend` instead of `.append` when adding to a global list
- `req.json()` returns a dictionary where `body["username"]` refers to the key `username`

starting aiohttp session
```Python
async with aiohttp.ClientSession() as session:
	async with session.get(url) as response:
```

**mcq**

file permissions
```
rwxrw-r--  me  us  /thing/
```
- User: `me` has permissions `rwx` or read, write, execute
- Group: `us` has permissions `rw` or read, write
- Others: has only `r` or read
- have to execute in the first two files and then read/write in the last

**docker definitions**

**Container:** run a program, get output, discard everything it did to my system
**DockerFile:** blueprint for creating an image
**Image:** used for creating and running containers 

docker run
- creates a container from an image and starts it
- runs something even if there is no program included after run/RUN
- same thing as opening an interactive docker shell

**docker scripting**

DockerFile:
- `FROM [image name]` initializes image by copying another image
- `RUN [shell command]` runs a command inside image during setup
- `COPY [path]` copies file or directory tree from computer inside image
- `USER [username]` runs any command that follows it and run in the image
- `WORKDIR [path]` DockerFile version of `cd`
- `CMD [shell command]` default command to run inside each container\

Create an image: `docker build -t [image name]`

Listing/Deleting images
- `docker images` lists all images usable by container
- `docker images --all` lists all images, even unnamed ones
- `docker rmi [image name]` removes single image
- `docker image prune` removes all "dangling" images
- `docker system prune --all`  removes any stopped containers and any images not used

Creating containers
- `-it` maps container's stdin, stdout and stderr to terminal
- `-p $X:$Y` causes network connections to port `$X` to be forwarded into container and remapped to port `$Y`
- `-v $X:$Y` causes directory `$X` to show up in the container as `$Y`, sees changes in the filesystem
- `--rm` remove container as long as it is finished running

Listing/Deleting containers
- `docker container ls` lists currently running containers
- `docker container ls --all` lists currently exiting containers (both running and finished)
- `docker container rm [container id]` removes container not running
- `docker container rm --force [container id]` removes container if running or not
- `docker container prune` removes all container not running

**X as a service**

FaaS
- serverless computing
- rest apis

SaaS
- Campuswire, Zoom

CaaS
- containers
- Docker

IaaS
- VirtualBox
- can do sudo permissions
