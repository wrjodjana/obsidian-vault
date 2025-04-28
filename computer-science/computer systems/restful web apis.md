
**Static server**:
- No computation of content
- Parses request, finds the file or precomputed information that has the answer, and responds with contents of that file

**Stateless server:**
- Computes part of the content, but only based on the current request
- Requests are not combined into sequences and do not interact with each other
- May contain some static information, but certain types of state are not stored

**Stateful server:**
- 