**cache variable:** defining a variable as a cache variable ensures that the value of that variable is not recalculated every time. This feature can help optimize the repetitive and time-consuming processes of the project's build process each time. 
- In this way, repetitive processes in the construction process are minimized and accelerated. 
- It is saved in the CMakeCache.txt file located in the build folder 
- Cache will not change even if we set the variable we specified in another place, it will remain constant. "FORCE" must be used to change or `cmake -Dvariable` with the -D parameter

**EVN:** used if we want to access an environment variable, change it, etc. 