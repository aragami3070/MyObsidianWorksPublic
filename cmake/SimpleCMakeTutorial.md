---
id: SimpleCmakeTutorial
aliases: []
tags: []
---

# Simple hello world
- Create a CMakeLists.txt file
- Simple hello world program
```CMake
cmake_minimum_required(VERSION 3.28)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(testCmake VERSION 1.0)
add_executable(hello main.cpp)
```

# Running CMake

- CMake from the command line.
```Terminal
cmake . && make && ./hello
```

# Adding a header file

- Slightly more involved program with header files. To include a header file directory:
```CMake
target_include_directories(hello PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
```

# Multiple source files (i don't like this method, I like libriry method)

- We can add source file like:
    - Now the CMake source explicitly discourages this but the "alternative" of listing every source file or using some other build system that generates your CMakeLists.txt files is perhaps even more cumbersome. So knowing all that, I'd recommend continuing to use glob until some sane alternative shows up:
```CMake
file(GLOB_RECURSE SRC_FILES src/*.cpp CONFIGURE_DEPENDS)
add_executable(hello ${SRC_FILES})
```

# My own libriry (I like this method)

- Create a lib from some source files 
```CMake
add_library(mylib STATIC lib/MyClass.cpp lib/MyClass.h)
```
- Can then include it in your main executable
```CMake
target_link_libraries(hello PUBLIC mylib)
```

Was write [[2024-09-15#2024-09-15 🗓]]

[Back to top](#top)
