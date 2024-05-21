## Enable macros via CMake

### Introduction
In order not to affect the running of the original code, we can control the running of the code through macro definitions and compilation parameters. This article will introduce how to enable macros through CMake.

### Example

#### Step 1: Add a macro definition in the code
```cpp
#include <iostream>

#ifdef ENABLE_IMU_MEASUREMENT
void performIMUMeasurement() {
    std::cout << "Performing IMU measurement..." << std::endl;
    int imuData = 42; 
    std::cout << "IMU Data: " << imuData << std::endl;
}
#endif

int main() {
    #ifdef ENABLE_IMU_MEASUREMENT
    performIMUMeasurement();
    #else
    std::cout << "IMU measurement is disabled." << std::endl;
    #endif
    return 0;
}
```

#### Step 2: Add a CMakeLists.txt file

```cmake
cmake_minimum_required(VERSION 3.10)
project(IMUProject)

option(ENABLE_IMU_MEASUREMENT "Enable IMU measurement" OFF)

if(ENABLE_IMU_MEASUREMENT)
    message(STATUS "Enable IMU measurement option is ON")
    add_definitions(-DENABLE_IMU_MEASUREMENT)
else()
    message(STATUS "Enable IMU measurement option is OFF")
endif()

...
```

#### Step 3: Build the project

```bash
cmake -DENABLE_IMU_MEASUREMENT=ON ..
make
```

#### Step 4: Check the output

Make sure the output is as expected.

```bash
-- Enable IMU measurement option is ON
-- Configuring done
-- Generating done
...
```

#### Conclusion
In this article, we introduced how to enable macros through CMake. By controlling the macro definition, we can control the running of the code. This is a good way to avoid affecting the original code.