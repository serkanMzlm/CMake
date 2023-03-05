
**set(varvariable_name variable1 variable2 ...)**: Creates a cmake array variable. ${} is used to access the value contained in a cmake variable. There is no obligation to mark with ". If " is omitted, each space moves to the next array element. If variables are specified in "${}" when calling, they will all be written contiguously if there is an array inside the variable. between arrays if called only with ${}; is separated as. instead of space when setting; same meaning can be used
- set(number 1 2 3) = set(number 1;2;3)
- set(name "aa;bb;cc") = set(name aa bb cc)

**set(varvariable_name variable1 variable2 ...)**: Creates a cmake array variable. ${} is used to access the value contained in a cmake variable. There is no obligation to mark with "". If "" is omitted, each space assign to the next array element.

**unset():** Makes the variable undefined

**message():** Allows output to the screen. The type of output can be determined
- message(STATUS "Cmake File Status Worked...")
- message(DEBUG "Cmake File Debug Worked...")
- message(WARNING "Cmake File WARNING Worked...")
- message(FATAL ERROR "Cmake File FATAL ERROR Worked...")
- message("Cmake File Worked...")

Run the command <u>cmake -P CmakeLists.txt</u> to run the cmake file without output
