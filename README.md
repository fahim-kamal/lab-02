# Lab 2
[Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repo and clone it to your machine to get started!

## Team Members
- Fahim Kamal


## Lab Question Answers

Answer for Question 1: When the 50% loss to my local enviornment was applied, 
the UDP became about 50% less reliable (12 #s received / 30 #s sent). The
UDP protocol does not ensure that all the packets that are sent are received.

Answer for Question 2: The reliability of TCP did not change. All of the messages
that were sent by the client were received by the server. This is because TCP
has the ability to resend a packet if it has been lost. The messages that were lost
were resent to the server. 

Answer for Question 3: The TCP response in the server was slower. At first, it appeared
that the TCP server did not receive the messages. However, after staying in the server
terminal window for a longer period of time, the messages were received. 

## Server Question Answers
1. What is argc and *argv[]?
Argc and *argv[] are parameters to the main function that are helpful for 
using command line arguments when a program is run. Argc is of type int and 
represents the number of arguments on the command line. *argv[] is a pointer
to a character array which holds the values entered on the command line. argv[0]
is the array that has the name of the program. 
(https://www.ibm.com/docs/en/i/7.1?topic=functions-main-function)

2. What is a UNIX file descriptor and file descriptor table?
A UNIX file descriptor is an index in the file descriptor table for a file. 
The file descriptor table holds pointers to all open input/output streams
that a process uses. By default, a process has three default points to stdin, 
stdout, and stderror. 
(https://www.youtube.com/watch?v=KM5sRWAYqaw)
(https://www.linuxhowtos.org/data/6/fd.txt)

3. What is a struct? What's the structure of sockaddr_in?
Structs are ways to different related variables together (does not have
to be of same type). Sockaddr_in has four members. The first member
is a short called sin_family which is an address from the internet.
There is an unsigned short variable called sin_port. There is a
struct in_addr and sin_addr. Lastly, there is a char called sin_zero[8].
(https://www.w3schools.com/cpp/cpp_structs.asp)

4. What are the input parameters and return value of socket()?
Socket() has three input parameters. The first parameter determines
what adress domain the socket is referencing. This can either be 
AF_UNIX or AF_INET (address from unix or adress from the internet).
The second argument defines the type of socket, whether it will be 
a continous stream (SOCK_STREAM) or if the message will be read in 
chunks (SOCK_DGRAM). The third argument is the type of comunication
protocol. Socket() returns an entry into the file descriptor table
that is used to later reference this socket. 

5. What are the input parameters of bind() and listen()?
Bind takes three input paramters. The first is the file descriptor of the socket. 
The second is address bound to the socket. The last is the size of the address. 
Listen() takes in the two parameter. The first is the file descriptor of the socket
and the last is the maximum amount of connections that are allowed to wait for the 
socket.

6.  Why use while(1)? Based on the code below, what problems might occur if there are 
    multiple simultaneous connections to handle?
The while loop is used to continuously listen for data to come in on the connection. This
can be problematic if there are multiple connections to handle because the program will be
stuck polling for data on one connection. It is not able to handle multiple connections at a
single time. 

7. Research how the command fork() works. How can it be applied here to better handle multiple connections?
Fork is a system call that allows a parent process to create a new process called a child process. Child
processes can run at the same time as the parent process. If we forked after a connection is established,
we would be able to use fork to simultaneous handle a connection and wait to accept another. The child process
would close the socketfd and pass the newsockfd of the client for subsequent commuincation. The parent process
would close the server socketfd and wait to accept another client. 
(https://www.geeksforgeeks.org/fork-system-call/)

8. This program makes several system calls such as 'bind', and 'listen.' What exactly is a system call?
System calls are ways programs are able to use services from the operating system. 
(https://en.wikipedia.org/wiki/System_call)

...
