**function(func_name , fanc_args):**  Even if we change the value of the global variable inside the function, this value does not change in the global area, but only in the local part. (this event is valid in add_subdirectory) keyword "PARENT_SCOPE" is used to change the value in the global field. PARENT_SCOPE changes the variable outside the function, not the one inside the function.

- ARGC how many arguments are entered
- ARGV a list with all the arguments
- ARGN Retrieves values ​​other than the values ​​the function takes as parameters
- ARG_number we specify the argument in whatever order we want

**macro(func_name , fanc_args):** everything counts as the same with the function, if the functions are converted to a macro, the code will run without error. The difference between them is that when a global variable value changes inside the macro function, its direct effect is on the variable outside. (No need to use PARENT_SCOPE)