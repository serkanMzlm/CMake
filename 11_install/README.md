**install():** Its main purpose is to copy the specified file to the desired location.
- FILES copies the file
- TARGETS directory copies
- EXPORT It converts the files we made into the necessary form to enable us to find them with the find_package command.


We copy the libraries we made in this project to certain parts in /usr/local and make them work in our other projects.

`
make
sudo make install  
`

Note: Without "sudo make install", the install parts we specified in cmake will not work. The reason for using sudo in this example is that the place where we are installing requires permission.

we can install the packages we use all the time to the **/usr/local/** directory

Header Files: /usr/local/include/<package_name>

Targets: /usr/local/lib/<package_name>