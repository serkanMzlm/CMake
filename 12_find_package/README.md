**find_package(ABC):**  It searches for ABC-config.cmake, the folder it's looking for is /usr/local/lib/ABC.
- With **REQUIRED**, we make it mandatory to have this file
- MODULE Used to search as a module find_package(my_lib MODULE) -> Findmy_lib.cmake
- CONFIG Used to search as a config find_package(my_lib MODULE) -> my_lib-config.cmake

Note: If not specified, it searches in MODULE mode first, then searches in CONFIG mode.