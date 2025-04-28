
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
4. **Uniform interface** - 