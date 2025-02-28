# MacOSProgram
MacOSProgram big nerd

refer page no: 287
# step 1:
first create unix.txt file 

first open Terminal and create .m file

using : vi append.m  // create append.m file

# step 2.
//write a program which open unix.txt file


#import <errno.h> // for errno and strerror()

#import <fcntl.h> // for open()

#import <stdio.h> // // for printf() and friends

#import <stdlib.h> // for EXIT_SUCCESS

#import <string.h> //// for strerror()

#import <unistd.h> // // for STDOUT_FILENO

int main (void)

  {

        close (STDOUT_FILENO);
        
        // open a log file, write only, and to always automatically append.
        
        // oh, and create the file if it doesn't exist already
        
        int fd = open ("unix.txt", O_WRONLY | O_CREAT | O_APPEND,S_IRUSR | S_IWUSR);
        
        if (fd == -1)
        {
                fprintf (stderr, "can't open log file. Error %d (%s)\n", errno, strerror(errno));
                return EXIT_FAILURE;
        }
        printf ("wheee, we have a log file open\n");
        
  return EXIT_SUCCESS;

  }

# step 3:

press esc :wq    //to save and exit from vi editor

# step 4 :
compile program 

gcc -g -Wall -o append append.m
//append.m file pass to compiler and compiler give executable file "append"

# step 5
./append   //run the program

Here are some runs of the program:

$ ls -l unix.txt

ls: unix.txt: No such file or directory

$ ./append

$ ls -l unix.txt

-rw------- 1 markd wheel 31

$ cat unix.txt

wheee, we have a log file open

$ ./append

$ ./append

$ cat unix.txt

wheee, we have a log file open 

wheee, we have a log file open 

wheee, we have a log file open


great you done it

