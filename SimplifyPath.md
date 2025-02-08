
## Simplify Path


You are given an absolute path for a Unix-style file system, which always begins with a slash '/'. Your task is to transform this absolute path into its simplified canonical path.

The rules of a Unix-style file system are as follows:

A single period '.' represents the current directory.
A double period '..' represents the previous/parent directory.
Multiple consecutive slashes such as '//' and '///' are treated as a single slash '/'.
Any sequence of periods that does not match the rules above should be treated as a valid directory or file name. For example, '...' and '....' are valid directory or file names.
The simplified canonical path should follow these rules:

The path must start with a single slash '/'.
Directories within the path must be separated by exactly one slash '/'.
The path must not end with a slash '/', unless it is the root directory.
The path must not have any single or double periods ('.' and '..') used to denote current or parent directories.
Return the simplified canonical path.

 

Example 1:

Input: path = "/home/"

Output: "/home"

Explanation:

The trailing slash should be removed.

Example 2:

Input: path = "/home//foo/"

Output: "/home/foo"

Explanation:

Multiple consecutive slashes are replaced by a single one.

Example 3:

Input: path = "/home/user/Documents/../Pictures"

Output: "/home/user/Pictures"

Explanation:

A double period ".." refers to the directory up a level (the parent directory).

Example 4:

Input: path = "/../"

Output: "/"

Explanation:

Going one level up from the root directory is not possible.

Example 5:

Input: path = "/.../a/../b/c/../d/./"

Output: "/.../b/d"

Explanation:

"..." is a valid name for a directory in this problem.

 

Constraints:

1 <= path.length <= 3000
path consists of English letters, digits, period '.', slash '/' or '_'.
path is a valid absolute Unix path.
### Approach 1: Stack

## Steps

1. Split the path into components
2. Iterate through the components
3. If the component is a "." or "", continue
4. If the component is a "..", pop the last component from the stack
5. Otherwise, push the component onto the stack

```javascript
var simplifyPath = function(path) {
    const stack = []; // Stack to store the valid directories
    const components = path.split("/"); // Split the path by '/'

    for (const component of components) {
        if (component === "" || component === ".") {
            // Ignore empty components and '.'
            continue;
        } else if (component === "..") {
            // '..' means go to the parent directory (pop the stack)
            if (stack.length > 0) {
                stack.pop();
            }
        } else {
            // Valid directory/file name; push it onto the stack
            stack.push(component);
        }
    }

    // Join the stack with '/' to form the canonical path
    return "/" + stack.join("/");
};

```




