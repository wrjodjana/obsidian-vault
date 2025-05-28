
**Static server**:
- No computation of content
- Parses request, finds the file or precomputed information that has the answer, and responds with contents of that file

**Stateless server:**
- Computes part of the content, but only based on the current request
- Requests are not combined into sequences and do not interact with each other
- May contain some static information, but certain types of state are not stored

**Stateful server:**
- Tracks different information for different clients
- Usually login function followed by a series of actions that interact with user's logged in data
- Usually contain some stateless and static information

### REST

**Definition:** representational state transfer with these 5 properties:
1. **Client / Server** - clients distinct with servers, interacting through a defined interface/API
2. **Stateless** - servers do not store per-client data
3. **Cache** - each response from the server indicates how long it may be cached
4. **Uniform interface** - request and responses formats use as similar format to one another as possible
5. **Layered system** - server is designed to be able to split into many separate computers, with clients unable to tell which computer responded or even if there are several of them

### RESTful Web API

**Properties:**
- Clients send HTTP requests, servers reply
- GET does not change server state, but POST changes existing server state
- PUT and DELETE can be used to create and remove server states, but POST can handle this
- HTTP request path identifies resource you are accessing
- HTTP request body describes specific changes being implemented
- HTTP headers may be used to pick response format, but not to change meaning of request
- All request bodies within a single API uses the JSON or XML format
- All response bodies provide structured data structure in JSON or XML format

### aiohttp webservices

**Parsing and Routing Requests:**
1. Set up a TCP/IP server (opening sockets)
2. Parse HTTP requests sent to it
3. Send those parsed requests to functions registered based on path and method
4. Send the results of the functions back to those who sent the requests, formatted as HTTP requests

**Third Step:**
1. Make routing table, which is a `dict` with `(method, host)` pairs as keys and functions as values:

```Python
from aiohttp import web
routes = web.RouteTableDef()
```

2. Decorate each function you write with the method and path to send it:

```Python
@routes.get("/path")
async def handle_path(req : web.Request) -> web.Response:
	return web.Response(status=500, text="Server Incomplete")
```

3. After defining functions, if running as program, make an app that uses those routes and start:

```Python
if __name__ == "__main__":
	app = web.Application()
	app.add_routes(routes)
	web.run_app(app)
```

- `run_app` opens server socket, accepts client sockets, parses any messages sent by client as HTTP requests,  compares the requests to the routes in `routes` and if finds a match calls that function, otherwise returns 404 NOT FOUND HTTP response

