# A webserver written in C that compiles to an 804-byte ELF file
This is achieved by:
* Using the tiny C compiler
* Compiling without the standard library, instead using inline assembly syscalls
* Using ld.gold
* Stripping the binary as much as possible
* Doing plenty of other weird things

# How shitty is this webserver?
It will crash after 1024 (i think) requests due to the open file limit.
This is a high quality design choice to minimise filesize.

It will also not properly close the listener socket, meaning you cannot properly restart it as it will fail to bind to the same port.
This is also a high quality design choice to minimise filesize.

# Todo if I ever bother
* Add some macro magic to enable/disable the silly space saving methods (such as the above mentioned crashes caused by not closing sockets/files)
