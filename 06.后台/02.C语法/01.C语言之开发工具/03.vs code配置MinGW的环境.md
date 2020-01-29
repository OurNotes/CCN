总操作流程：
- 1、创建项目文件夹
- 2、创建配置文件

***
# 创建项目文件夹

- test
    -.vscode

# 创建配置文件

- tasks.json

```json
{
    "version":"2.0.0",
    "command": "g++",
    "args": ["-g","-std=c++11","${file}","-o","${workspaceRoot}\\${fileBasenameNoExtension}.exe"],
    "problemMatcher": {
        "owner": "cpp",
        "fileLocation": ["relative", "${workspaceRoot}"],
        "pattern": {
            "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning|error):\\s+(.*)$",
            "file": 1,
            "line": 2,
            "column": 3,
            "severity": 4,
            "message": 5
        }
    }
}
```

- launch.json

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Launch",                
            "type": "cppdbg",                         
            "request": "launch",                        
            "targetArchitecture": "x86",                
            "program": "${workspaceRoot}\\${fileBasenameNoExtension}.exe",                 
            "miDebuggerPath":"C:\\Software\\MinGW\\bin\\gdb.exe", 
            "args": [],     
            "stopAtEntry": false,                  
            "cwd": "${workspaceRoot}",                  
            "externalConsole": true,                  
            "preLaunchTask": "g++"　　                  
            }
    ]
 }

```

