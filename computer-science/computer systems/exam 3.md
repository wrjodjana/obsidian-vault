
**coding**

rest api template
```Python
@routes.post("/") 
async def func(req : Request) -> Response:
	return Response()
```
- post could be replaced with put, get, delete
- response can have headers `status`, `text`

reading request body
```Python
text = await req.text()
```
- to call the request body u use `await`
- `req.text()` is used to read the request body


