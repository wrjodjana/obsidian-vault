
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


**mcq**

file permissions
```
rwxrw-r--  me  us  /thing/
```
- User: `me` has permissions `rwx` or read, write, execute
- Group: `us` has permissions `rw` or read, write
- Others: has only `r` or read

docker definitions

**Container:** run a program, get output, discard everything it did to my system
**DockerFile:** blueprint for creating an image
**Image:** used for creating and running containers 

docker run
- creates a container from an image and starts it
- runs something even if there is no program included after run/RUN
- same thing as opening an interactive docker shell

DockerFile RUN
- executes commands in a new layer on top of the image
- usually used for setup commands like `apt-get install`

Both
- contains side effects of the program to be inside Docker

docker cli flags

`-it`
- maps the container's stdin, stdout and stderr to the terminal

`--rm`
- removes the container as long as we are finished running it

`-p $X:$Y`
- causes network connections to port `$X` to be forwarded into container and remapped to port `$Y` inside it
- connects a socket to it through a browser

`-v $X:$Y`
- causes directory `$X` on your disk to show up in the container as `$Y`
- allows to see changes we make in our filesystem