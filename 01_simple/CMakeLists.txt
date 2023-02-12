cmake_minimum_required(VERSION 3.10)  #Sets the minimum cmake version to run cmake
project(myProject LANGUAGES C CXX ASM VERSION 1.0) #Set the version, project name and languages ​​used in the project for the project.
add_executable(my_project 
                main.cpp
                add.hpp 
                add.cpp) #sets the files that need to be compiled for the executable and sets the name of the resulting file