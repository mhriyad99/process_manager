# PMFlow
<p style="font-size:15px;">This is a simple process managing tool</p>

<p style="font-size:15px;">This tools keeps the information of the processes it manages in a json file created at it's installation location</p>

## Installation
```
pip install pmflow
```
## Commands
### <^> Main commands
create: Creates a new process

Required arguments:
- command: str (default: None)

Optional arguments:
- --name or -n : str (default: None)
- --group or -g : str (default: process_id)
- --relation or -r : "parent" | "child" (default: "parent")
- --verbose or -v: (default: false)

Note: A child process must have a group name and the group must have a parent process.

Example:
```
pm create "<command>"
or
pm create "<command>" -n "<process name>" -g "<group name>" -r "child"
```
ls: List all managed processes

Optional arguments:
- --json or -j (default: false)
- --group or -g (default: None)
- 
Example:
```
pm ls
pm ls -j
pm ls -g <group_name>
pm ls -j -g <group_name>
```
kill: Kill process, kills the process and also removes it from the json file.

Optional arguments:
- pid (no flag needed): int (default: 0) kills one process if it's a child process. Otherwise, kills the terminates 
- --group or -g: <group name> (default: None) kills one group if exist
- --all or -a : bool (default: false) kills all the process

Note: Only one option can be used at a time.

Example:
```
pm kill <PID>
pm -g <group_name>
pm -a
```
### <^> Additional commands
Recreate all process managed by the tool:
```
pm recreate
```
Pause a process
```
pm pause <PID>
```
respawn all paused process
```
pm respawn
```
