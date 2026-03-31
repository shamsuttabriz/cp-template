# CP Terminal Setup Guide (VS Code + GCC)

This guide explains how to set up a Competitive Programming (CP) environment using VS Code, GCC, and terminal automation.


## Step-by-Step Setup

### ✅ Step 1–3: Install VS Code
1. Install VS Code for your system (Ubuntu, Debian, Fedora, etc.)
2. Download from: https://code.visualstudio.com/download
3. Instal and go to the folder where download the file


### ✅ Step 4–5: Install VS Code
4. Copy your downloaded file name  
5. Run:
```bash
sudo apt install ./your-vscode-file-name.deb
```


### ✅ Step 6–7: Install GCC Compiler
6. Install compiler:
```bash
sudo apt install gcc     # Ubuntu/Debian
sudo dnf install gcc     # Fedora
```

7. Check version:
```bash
gcc --version
```


### ✅ Step 8–9: Create Project
8. Open VS Code and create a folder  
9. Create a file like `test.c` or `basic.c`


### ✅ Step 10–11: Install Extensions
Install these extensions:
- C/C++ (Microsoft)
- Code Runner (Jun Han)
- C/C++ Extension Pack (Microsoft)
- C/C++ Compiler Run (danielpinto8zz6)


### ✅ Step 12–13: Write and Run Code

Example:
```c
#include<stdio.h>

int main() {
    printf("Hello World!\n");
    return 0;
}
```

- Save file  
- Click Run → Output will show in terminal  


### ✅ Step 14: Create Files
Create:
- `input.txt`
- `output.txt`


### ✅ Step 15–16: Configure tasks.json

Go to:
- Terminal → Configure Tasks → Open `tasks.json`

Replace with:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Compile and run",
      "type": "shell",
      "command": "",
      "args": [
        "g++",
        "-g",
        "${relativeFile}",
        "-o",
        "${fileBasenameNoExtension}.out",
        "&&",
        "clear",
        "&&",
        "timeout",
        "10",
        "/usr/bin/time",
        "-v",
        "--output",
        "sys.txt",
        "./${fileBasenameNoExtension}.out",
        "<",
        "input.txt",
        ">",
        "output.txt",
        "&&",
        "rm",
        "*out"
      ],
      "presentation": {
        "reveal": "silent"
      },
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "problemMatcher": {
        "owner": "cpp",
        "fileLocation": [
          "relative",
          "${workspaceRoot}"
        ],
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
  ]
}
```


### ✅ Step 17: Run Program

Open `.c` file and press:

```bash
Ctrl + Shift + B
```

✔ Output → `output.txt`  
✔ Execution stats → `sys.txt`  


## 📂 Folder Structure

```
cp-template/
│
├── test.c
├── input.txt
├── output.txt
├── sys.txt
└── .vscode/
    └── tasks.json
```


## 🎯 Features

- Fast compile & run  
- Input/output automation  
- Time & memory tracking  
- Clean workflow  


## 🏁 THINK.SOLVE.CODE!