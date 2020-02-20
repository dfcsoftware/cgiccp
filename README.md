# cgiccp
This sample describe how you can build web-based CGI applications that can interface with electronics hardware that is attached to the BeagleBone using Bash scripts that call C/C++ programs. 
The solution works well for very straightforward applications, but this discussion investigates more advanced solutions for applications where there are more complex interactions — for example, the use of web forms to pass data between your web browser and the application that is executing on the BeagleBone. In this discussion I begin by explaining how you can use a C/C++ program, rather than a CGI script, to display a web page. I then investigate the use of the GNU Cgicc library for more structured and complex interactions.

The approach describe here will work on any Linux machine, including other embedded platforms such as the Raspberry PI; however, the steps are structured for the BeagleBone platform and the examples that interact with the hardware are specific to the BeagleBone platform — they can however be easily modified. In this example, the Apache server is used to serve the CGI applications, so having Apache installed is the only prerequisite software required. Apache runs on port 8080 of the BeagleBone by default when using the recommended Debian images — you can test that by opening a web browser and entering the IP address of your Beaglebone in the address bar using the following format: http://192.168.7.2:8080/ (replace the IP address with your BeagleBone’s IP address — the one listed is the default IP address for Internet-over-USB).

It could be argued that this is a “dated approach” to solving the problem of having an embedded system web server interact with a web browser client — it has been around since the 1990’s. To some extent that is true. There are powerful alternatives available such as Java servlets, node.js, Dart, PHP etc. However, this approach:

    1-has a low overhead on the BeagleBone, as the code is compiled rather than interpreted.
    
    2-permits access to system calls
    
    3-can interface readily with hardware using the code libraries of CGI C++
