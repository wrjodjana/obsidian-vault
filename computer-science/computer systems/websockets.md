
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
allws[myid]
```