# Lessons Learned: GitHub API Operations

This repository documents key lessons learned while working with GitHub's API through Claude MCP (Model Control Protocol). These insights were gathered through practical experience with file operations and error handling.

## Key Findings

### 1. Error Messages vs Reality
- API error messages don't always indicate operation failure
- Operations may succeed despite error responses
- Always verify changes directly in the repository
- Don't rely solely on API response messages for status

### 2. SHA Handling
- Each file version has a unique SHA identifier
- Current SHA is required for file updates
- Successful updates generate new SHAs
- Using outdated SHAs results in "Conflict" errors
- Always get latest SHA before attempting updates

### 3. Content Formatting
- Content can be sent as plain text with UTF-8 encoding
- Base64 encoding is also supported
- Be careful with JSON structures - they will be literally written to the file
- API expects specific parameters like `content.encoding` and `content.content`
- Proper encoding declaration is essential

### 4. Best Practices
- Get latest file info before updates
- Track new SHAs after successful updates
- Verify changes in the repository
- Test with small changes first
- Keep track of the operation's actual effects
- Document unexpected behaviors

### 5. Important API Parameters
- `sha`: Current file's SHA (required for updates)
- `path`: File path in the repository
- `content`: New content to be written
- `message`: Commit message
- `branch`: Target branch (usually 'main')
- `encoding`: Content encoding type (e.g., 'utf-8', 'base64')

## Real-World Example
A typical file update process might look like this:

1. Get current file info to obtain SHA
2. Prepare new content with proper encoding
3. Submit update with current SHA
4. Verify changes in repository
5. Note new SHA for future operations

Even if you get error messages like `Invalid arguments: content.encoding: Required` or `GitHub API error: Conflict`, check the repository as the operation may have succeeded.

---
*This documentation was created through interactions with Claude AI, documenting real experiences with GitHub's API integration.*