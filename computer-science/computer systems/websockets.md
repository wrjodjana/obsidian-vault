
**Initiated messages on the web**
- **Polling:** 
- **WebSockets:** transitioning from HTTP's request-and-response use of TCP to a general open socket

**Server code:**
- `aiohttp` code because WebSocket requests initially look like HTTP requests:
```Python
@routes.get("/ws")
async def websocket_handler(request):
```
- 