
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

**DockerFile:** 
