Download Link: https://assignmentchef.com/product/solved-coen146l-lab-1-unix-linux-commands-and-overview-of-c-programming
<br>
<h5><strong>Unix</strong><strong>/ Linux</strong></h5>

<h5>Linux is a Unix-like operating system, following the design principles of Unix monolithic kernel in process control, cpu scheduling, memory management, file systems, networking, and access to the peripherals. Please read details on <a href="https://en.wikipedia.org/wiki/Linux">https://en.wikipedia.org/wiki/Linux</a>.Unix/ Linux has a culture of distinctive art and powerful design philosophy since its inception in 1969. Software technologies come and go but Unix/ Linux remained dominant and continued to evolve on a wide variety of machines ranging from supercomputers and PCs to handheld devices and embedded networking hardware.  C language is ubiquitous and a central technology of Unix/ Linux. It is very hard to imagine developing applications at the core system level without C. The POSIX, Portable Operating System Standard, the Unix API (Application Programming Interface) is used to write truly portable software that can run across a heterogeneous mix of computers. TCP/IP (which you will learn in this class) and Unix represent the core technologies of the Internet. For more details, see <a href="#_ftn1" name="_ftnref1">[1]</a>.</h5>

<h5></h5>

<h5>It is recommended that you install Linux on your, either as a bare operating system or as a virtual machine. For details, please check https://www.linux.com. If you are using Mac OS, you can use Linux commands in a terminal window, including vi and gcc compiler.</h5>




<strong>Command-line </strong>

<h5>The use of command-line programs is a tradition in UnixLinux. Commands are executable programs that can run with variety of arguments (options). Command-line options are single letters preceded by a single hyphen, including:</h5>

<h5>-a: all, -b: buffer, -c: command, -d: debug, -e: execute, -f: file, -l: list, -o: output, -u: user</h5>

<h5></h5>

Some of the basic commands are:




<ul>

 <li>ls: lists all files and directories (try with options: -a, -al)</li>

 <li>cat: displays file content (try cat file1 file2 &gt; file3)</li>

 <li>mv: moves a file to a new location (try mv file1 file2)</li>

 <li>rm: deletes a file</li>

 <li>cp: copy file</li>

 <li>man: gives help information on a command</li>

 <li>history: gives a list of past commands</li>

 <li>clear: clear the terminal</li>

 <li>mkdir: creates a new directory</li>

 <li>rmdir: deletes a directory</li>

 <li>echo: writes arguments to the standard output (try echo ‘Hello World’ &gt; myfile)</li>

 <li>df: shows disk usage</li>

 <li>apt -get: install and update packages</li>

 <li>mail -s ‘subject’ -c ‘cc-address’ -b ‘bcc-address’ ‘to-address’ &lt; filename: sends email with attachment</li>

 <li>chown/ chmod: change ownership/ permission of file or directory</li>

 <li>date: show the current date and time</li>

 <li>ps: displays active processes</li>

 <li>kill: kills process</li>

 <li>sh: bourne shell – command interpreter (good to learn about shell programming)</li>

 <li>grep: searches for pattern in files</li>

 <li>Ctrl+c: halts current command</li>

 <li>Ctrl+z: stops current command and resumes with foreground</li>

 <li>Ctrl+d (exit): logout of current session</li>

</ul>

<h5><strong> </strong></h5>

<strong>System calls </strong>

<h5>System calls are often called kernel calls. They are c libraries that execute at the kernel level to allow users to interact with the operating system for services that include:</h5>




<ul>

 <li>Process creation and management (e.g. fork(), exec(), wait(), exit())</li>

 <li>File management (e.g. open(), read(), write(), close())</li>

 <li>Communication (e.g. pipe(), shmget(), mmap())</li>

 <li>Networking (e.g. socket(), bind(), connect(), listen(), sendto(), recvfrom())</li>

</ul>




<strong>C Program with two processes</strong>

Demonstrate each of the following steps to the TA to get a grade on this part of the lab assignment

<ul>

 <li>[5%] Write the following C program in a Linux environment using vi, nano, emacs, or an editor of your choice</li>

</ul>

/*Sample C program for Lab assignment 1*/

#include &lt;stdio.h&gt;      /* printf, stderr */

#include &lt;sys/types.h&gt;  /* pid_t */

#include &lt;unistd.h&gt;     /* fork */

#include &lt;stdlib.h&gt;     /* atoi */

#include &lt;errno.h&gt;      /* errno */

/* main function with command-line arguments to pass */

int main(int argc, char *argv[]) {

pid_t  pid;

int i, n = atoi(argv[1]); // n microseconds to input from keyboard for delay

printf(“
 Before forking.
”);

pid = fork();

if (pid == -1) {

fprintf(stderr, “can’t fork, error %d
”, errno);

}

if (pid){

// Parent process

for (i=0;i&lt;100;i++) {

printf(“t t t Parent Process %d 
”,i);

usleep(n);

}

}

else{

// Child process

for (i=0;i&lt;100;i++) {

printf(“Child process %d
”,i);

usleep(n);

}

}

return 0;

}




<ul>

 <li>[5%] Compile the program using gcc compiler by typing gcc YourProgram.c – o ExecutableName. When it compiles without errors or warnings, make a copy of the source file then go to step 3.</li>

</ul>




<ul>

 <li>[5%] Run the program by typing ./ExecutableName and take a note of your observation.</li>

</ul>




<ul>

 <li>[10%] Re-run the program by typing ./ExecutableName Note that the delay in the loop depends on the command line argument you give, here the delay is 3000 microseconds.</li>

</ul>




<ol>

 <li>Enter delays of 500 and 5000, what happens?</li>

</ol>




<ul>

 <li>[30%] Rewrite the program in Step 1. with two threads instead of two processes, then demonstrate steps 1 – 3 to the TA. Include the pthread.h library and use the function pthread_create () instead of fork().</li>

</ul>

#include &lt;pthread.h&gt;

int pthread_create(pthread_t *thread, pthread_attr_t *attr,

void *(*start_routine) (void *arg), void *arg);




When your program compiles without errors or warnings, make a copy of the source file




Note: you will most probably use – ls, more, mv, rm, mkdir, rmdir, cd, cp, chmod, who, ps, kill, ctrl+c, cmp, grep, cat, and man – commands in linux.  Type man cat in the command line to learn about cat command, as an example.




<h5><strong>Circuit switching and packet switching</strong></h5>

Write a C program that implements quantitative comparisons between circuit switching and packet switching according to the following description

<u> </u>

<u>Variables</u>

<ul>

 <li>The bandwidth of a network link is denoted by int linkBandwidth;</li>

 <li>The bandwidth required for a given user is denoted by int userBandwidth;</li>

 <li>The number of circuit switching users is denoted by int nCSusers;</li>

 <li>The number of packet switching users is denoted by int nPSusers;</li>

 <li>The percentage of time a packet switching user needs to transmit is denoted by double tPSuser;</li>

 <li>The probability that a given (<em>specific</em>) packet switching user is busy transmitting is denoted by double pPSusersBusy;</li>

 <li>The probability that one (<em>specific</em>) packet switching user is not busy transmitting is denoted by double pPSusersNotBusy;</li>

</ul>




<u>Scenarios: </u>Consider the following two scenarios:

<ol>

 <li>A circuit-switching scenario in whichnCSusers users, each requiring a bandwidth of userBandwidth Mbps, must share a link of capacity linkBandwidth</li>

 <li>A packet-switching scenario withnPSusers users sharing a linkBandwidth Mbps link, where each user again requires userBandwidth Mbps when transmitting, but only needs to transmit at a percentage of tPSuser.</li>

</ol>

<u>Computations:</u>




<ul>

 <li>[15%] Circuit switching scenario

  <ol>

   <li>The number of circuit-switched users that can be supported is computed as follows:</li>

  </ol></li>

</ul>

nCSusers = linkBandwidth/ userBandwidth;




<ul>

 <li>[30%] Packet switching scenario

  <ol>

   <li>The probability that a given (<em>specific</em>) user is busy transmitting is computed as:</li>

  </ol></li>

</ul>

pPSusers = tPSusers;




<ol>

 <li>The probability that one specific other user is not busy is computed as:</li>

</ol>

pPSusersNotBusy = 1 – pPSusers;




<ol>

 <li>The probability that <em>all</em> of the other specific other users are not busy is computed as:</li>

</ol>

(1 – pPSusers)<em><sup> nPSusers -1</sup></em>;




<ol>

 <li>The probability that one specific user is transmitting and the remaining users are not transmitting iscomputed as:</li>

</ol>

<em>pPSusers</em><em><sup>1</sup></em> * pPSusersNotBusy<em> <sup>nPSusers -1</sup></em>




<ol>

 <li>The probability that exactly one (anyone) of the nPSusers users is busy is  pPSusers times the probability that a given specific user is transmitting and the remaining users are not transmitting, i.e.:</li>

</ol>

nPSusers *(<em> pPSusers</em><em><sup>1</sup></em> * pPSusersNotBusy<em> <sup>nPSusers -1</sup></em>)




<ol>

 <li>The probability that 10 specific users of nPSusersare transmitting and the others are idle is computed as:</li>

</ol>

<em>pPSusers</em><em><sup>10</sup></em> * pPSusersNotBusy<em> <sup>nPSusers -10</sup></em>




<ol>

 <li>The probability that any 10 users of nPSusersare transmitting and the others are idle is computed as:</li>

</ol>

(nPSusers, 10) * <em>pPSusers</em><em><sup>10</sup></em> * pPSusersNotBusy<em> <sup>nPSusers -10</sup></em>, where

(nPSusers, 10) = nPSusers!/(10!*(nPSusers – 10)!) co-efficient of binomial distribution




<ol>

 <li>The probability that more than 10 users of nPSusersare transmitting and the others are idle is computed as:</li>

</ol>

Σ <em><sub>i=11..nPSusers</sub></em> (nPSusers, i) * <em>pPSusers</em><em><sup>i</sup></em> * pPSusersNotBusy<em> <sup>nPSusers -i</sup></em>




Demonstrate steps 6 and 7 for your program to the TA with the following inputs:

linkBandwidth = 200 Mbps

userBandwidth = 20 Mbps

tPSuser  = 0.10

nPSusers = 19

<a href="#_ftnref1" name="_ftn1">[1]</a> Eric S. Raymond, <em>The Art of Unix Programming</em>, Pearson, 2004