# CMAKE
**CMAKE** is an open source system that allows the build process to be built independently of the operating system and the compiler.
1. "#" comment information
2. "#[==[ . . . ]==]" multiple comment lines
3. Commands are not case sensitive. PROJECT() = ProJect() = project()
4. `cmake --help`
5. `cmake --help-variable-list`  Returns the list of variables defined by default.
6. `cmake --help-variable PROJECT_BINARY_DIR` Returns information about the specified variables.
7. `$ENV{PATH}` Allows access to environment variables
8. The **-G** parameter determines what the build type will be. `cmake .. -G Ninja` ,  `cmake .. -G "Unix Makefiles"` ...
9. With the **-D** parameter, values ​​are assigned to the variables. For example, thanks to the DCMAKE_BUILD_TYPE parameter, the build is set. release debug... `cmake -DCMAKE_BUILD_TYPE=Release`

Build with Cmake
```
mkdir build
cd build
cmake ..
make 
```
or
```
cmake -B build  
cmake --build build
```
or 
```
cmake -S . -B build
cd build 
make 
```
------

### COMMANDS:
- cmake_minimum_required
- project
- add_executable
- add_library
- add_subdirectory
- target_link_libraries
- target_include_directories
- message
- set
- list
- string
- if-elseif-else-endif
- foreach
- while
- function
- macro
- cache variable
- install
- find_package
---------

### MACROS:
- PROJECT_NAME       = The name specified in the project() command
- CMAKE_PROJECT_NAME = Project name found in top directory
- CMAKE_VERSION      = Cmake version (3.16.1)
    - CMAKE_MAJOR_VERSION 3
    - CMAKE_MINOR_VERSION 16
    - CMAKE_PATCH_VERSION 1
- CMAKE_GENERATOR    = Cmake build shape (ninja makefiles...)