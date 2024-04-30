## Enable ROS  Debug

### 1. Complie with Debug mode

* add `-DCMAKE_BUILD_TYPE=Debug` to `catkin_make` command

```bash
catkin_make -DCMAKE_BUILD_TYPE=Debug
```

* or update the `CMakeLists.txt` file

```cmake
SET(CMAKE_BUILD_TYPE "Debug")
SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb")
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")
```

### 2. Launch ROS with Debug mode

* GDB run ros node

```bash
gdb <executable>
```

* add `--prefix` in `rosrun` command

```bash
rosrun <package> <executable> --prefix 'gdb -ex run --args'
```

* use VSCODE to debug ROS node

  1. compose a `launch.json` file in `.vscode` folder(confirm the path of the **executable** file), example is shown below.
  
  2. run the debug configuration in VSCODE

  3. set breakpoints in the code

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "ROS Debug",
      "type": "cppdbg",
      "request": "launch",
      "program": "${workspaceFolder}/devel/lib/dynamic_biped/highlyDynamicRobot_node",
      "args": [],
      "stopAtEntry": false,
      "cwd": "${workspaceFolder}",
      "environment": [],
      "externalConsole": false,
      "MIMode": "gdb",
      "setupCommands": [
        {
          "description": "Enable pretty-printing for gdb",
          "text": "-enable-pretty-printing",
          "ignoreFailures": true
        }
      ],
    }
  ]
}

```

