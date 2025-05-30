
**Initiated messages on the web**
- **Polling:** 
- **WebSockets:** transitioning from HTTP's request-and-response use of TCP to a general open socket

**Server code:**

- `aiohttp` code because WebSocket requests initially look like HTTP requests:
```Python
@routes.get("/ws")
async def websocket_handler(request):
```

-  Create a WebSocket connection object and waiting while it communicates with the client:
```Python
ws = web.WebSocketResponse()
await ws.prepare(request)
```

- Keeping tracking of all connected WebSockets
```Python
global nextid
global allws
myid = nextid
nextid += 1
allws[myid] = ws
```

- Read messages sent by the client, forwarding them to all other clients
```Python
async for msg in ws:
	if msg.type == WSMsgType.TEXT:
		for other in allws:
			await allws[other].send_str(f'{my id} : {msg.data}')
	elif msg.type == WSMsgType.ERROR:
		print(f'ws {my id} recieved exception {ws.exception()}')

	del allws[my id]
	return ws
```

- When the app shuts down, we need to let it know it's OK to shut down the ope n WebSockets
```Python
async def shutdown_ws(app):
	for other in tuple(allws):
		await allws[other].close()

if __name__ == '__main__':
	app = web.Application()
	app.add_routes(routes)
	app.on_shutdown.append(shutdown_ws)
```