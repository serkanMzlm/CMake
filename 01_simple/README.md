**cmake_minimum_required(VERSION {cmake version}) :** In order for the cmake file to run, the minimum cmake version to be used in the operating system is determined. If the specified version does not exist, it returns an error.

**project(project_name LANGUAGES _ _ VERSION _) :** The Cmake project is given a name. and also the languages ​​used in the project and the project version can be adjusted optionally.

**add_executable(my_project main.cpp . . . ):** We set the files we want to be compiled and we specify the name of the executable that will be created in the first parameter.
