**set(varvariable_name variable1 variable2 ...)**: Creates a cmake array variable. ${} is used to access the value contained in a cmake variable. There is no obligation to mark with "". If "" is omitted, each space assign to the next array element.

**message():** Allows output to the screen. The type of output can be determined
- message(STATUS "Cmake File Status Worked...")
- message(DEBUG "Cmake File Debug Worked...")
- message(WARNING "Cmake File WARNING Worked...")
- message(FATAL ERROR "Cmake File FATAL ERROR Worked...")
- message("Cmake File Worked...")
