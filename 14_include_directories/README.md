**target_include_directories(my_libs PUBLIC ${PROJECT_SOURCE_DIR}/inc):** Specifies the directory where the .h files are located. Keywords such as PUBLIC , PRIVATE , INTERFACE can be used.  <u>PROJECT_SOURCE_DIR</u> (project directory)
- PUBLIC   : If used in both executable and library
- PRIVATE  : Only if used in library
- INTERFACE: If not used in library but used in executable file 

Multiple PUBLIC PRIVATE can be used within this command. target_include_directories(my_libs PUBLIC xxx PRIVATE yyy INTERFACE zzz) 


**include_directories(${PROJECT_SOURCE_DIR}/inc):** shows the location of the project's libraries.

difference between include_directories and target_include_directories:
- The "include_directories" function makes the given directories valid for all targets of the project. This will make all source files of the project find header files containing given directories
- The "target_include_directories" function makes the given directories valid only for a specified target. This ensures that it only finds the header used by the specified target and prevents the other target from using the given directories.
