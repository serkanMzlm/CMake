**target_include_directories(my_libs PUBLIC ${PROJECT_SOURCE_DIR}/inc):** Specifies the directory where the .h files are located. Keywords such as PUBLIC , PRIVATE , INTERFACE can be used.  <u>PROJECT_SOURCE_DIR</u> (project directory)
- PUBLIC   : If used in both executable and library
- PRIVATE  : Only if used in library
- INTERFACE: If not used in library but used in executable file 

Multiple PUBLIC PRIVATE can be used within this command. target_include_directories(my_libs PUBLIC xxx PRIVATE yyy INTERFACE zzz) 
