# Bash Scripting (CheatSheet)
- [x] shebang #! + bashPath(which bash)
- [x] chmod +x filename.sh
- [x] Capturing output from shell cat >
- [x] execute bash script ./filename.sh
- [x] Append content to existing file cat >>
- [x] Conditional,Loops,If-elif,AND(&&) OR(||) 
- [x] Break & Continue
- [x] Script input (Single/Multiple args=("$@"))

>  First Bash Script

- 'cat /etc/shells' -> to see all the available shell on system.
                
                /bin/sh
                /bin/bash # use this
                /bin/rbash
                /bin/dash
                /usr/bin/screen

- 'which bash' -> to know the path of the bash.

- so every script we write we add the path i.e /bin/bash to that script.

- write bash scripts in .sh file extensions



            --sample1.sh--

            #! /bin/bash

            echo "hello bash scripting"

- remember to make the newly created .sh executables, +x executable permission

            chmod +x sample1.sh
            ls -al

            # output
            rwxr-xr-x    sample1.sh

- finally to execute bash file ./fileName.sh
            
             ./sample1.sh

             # output
             hello bash scripting

---



            --sample1.sh--
            #! /bin/bash

            echo "hello bash scripting" > file.txt

- after executing the above script a new file.txt will be created with content as hello bash scripting inside of it

            ./sample1.sh

            cat file.txt
            # output
            hello bash scripting

> Capturing the output from shell and write it to a file using >

        ./sample1.sh

        #! /bin/bash
        cat > file.txt

- after executing above script we can write anything in the bash and then to exit press ctrl+d.

        ./sample1.sh
        I am talking via the bash shell

        cat file.txt
        # will have the text that we wrote in the shell when we executed ./sample1.sh
        # inside file.txt
        I am talking via the bash shell

> Appending Captured text from shell to existing file 

- If we dont want to overwrite the content instead append the content then use >>
        
        ./sample1.sh

        #! /bin/bash
        cat >> file.txt

        ./sample1.sh
        this is appended text

        cat file.txt
        # will have the text that we wrote in the shell when we executed ./sample1.sh
        # inside file.txt
        I am talking via the bash shellthis is appended text

> Comments in bash

- single line comment #

            # this is a single line comment

- multiline 
        
        : 'this is multiline comment
        use this effectively'

---

> Conditional Statements

- if [ condition ] then else fi
- -eq (equal)

            --sample1.sh--
            
            #! /bin/bash
            count=10;
            if [ $count -eq 10 ]
            then
                echo "Condition true"
            else
                echo "Condition false"
            fi

            ./sample1.sh
            # output
            Condition true
- -ne(not equal)

            count=10
            if [ $count -ne 0 ]
            then
                echo "counter has been altered"
            else
                echo "Counter intact"
            fi

            ./sample.sh
            # output
            counter has been altered

- -gt or > (greater than)
- note if using > then use (())

            if (( $count > 10 ))

- < (less than)

            if(( $count < 10> ))

- if elif statements

            if (( $count>10 ))
            then
                echo "Number greater than 10"
            elif (( $count<10 ))
            then
                echo "Number lesser than 10"
            else
                echo "Number is equal to 10"
            fi

- (and operator) && or -a

            age=21
            if [ $age -gt 18 ] && [ $age -lt 30 ]
            then
                echo "Peak time of the life"
            else
                echo "you are almost their towards the end"
            fi

            # or

            age=21
            if [ $age -gt 18  -a  $age -lt 30 ]
            then
                echo "Peak time of the life"
            else
                echo "you are almost their towards the end"
            fi

- (OR Operator) 

        # -o
        [condition1 -o condition2] 
         
        # || 
        [ condition1 ] || [ condition2 ]

---

>  Loops (while,until,for)

                # while loop
                # Syntax - while [ condition ] do done

                # example
                number=1
                while [ $number -lt 10 ]
                do 
                    echo "$number"
                    number=$(( number+1 ))        
                done


                # until loop
                # it executes the code until the condition mentioned is false or we can say until loop stops  when the condition mentioned is achieved.
                
                number=1
                until [ $number -ge 10 ]
                do 
                    echo "$number"
                    number=$(( number+1 ))        
                done

                # output for until loop
                1
                2
                3
                4
                5
                6
                7
                8
                9


                # for loop
                # syntax for i in 1 2 3 4 5 do done
                for i in 1 2 3 4 5
                do
                    echo $i
                done

                # output
                1
                2
                3
                4
                5

                # for a particular range say from 0 to 20 times
                for i in {0..20}
                do
                    echo $i
                done

                # output
                1
                2
                3
                ..
                ..
                20

                # adding increment
                # {start..ending..increment}
                for i in {0..20..2}
                do
                    echo "$i"
                done

                # output
                0
                2
                4
                6
                ..
                20

                # the conventional way
                for (( i=0; i<5;i++ ))
                do
                    echo "$i"
                done

                #output
                0
                1
                2
                3
                4

---

> Break & Continue

                # loop breaks when i becomes 6
                for (( i=0;i<10;i++ ))
                do
                    if [ $i -gt 5 ]
                    then
                        break
                    fi
                    echo $i
                done

                #output
                0
                1
                2
                3
                4
                5

                # continue(skipping a particular iteration)
                for (( i=0;i<10;i++ ))
                do
                    if [ $i -eq 9 ] || [ $i -eq 5 ]
                    then
                        continue
                    fi
                    echo $i
                done

                # output
                0
                1
                2
                3
                4
                6
                7
                8

---
 
> Script Input "$@"

            # Script Input takes three inputs
            echo $1 $2 $3

            ./hello.sh BMW TOYOTA MERCEDES
            # the BMW, TOYOTA and MERCEDES will get stored in $1,$2 & $3 respectively

            # we can also print the file name

            echo $0 $1 $2 $3
            ./hello.sh BMW TOYOTA MERCEDES

            #output
            ./hello.sh BMW TOYOTA MERCEDES 
            

            # IMPORTANT
            # to get an array/multiple of inputs
            # args = ("$@")
            # $0 specifies any number of inputs
            # $3 specifies 3 inputs allowed only
            
            # --hello.sh--
            args = ("$@")
            echo $@ 
            # prints all inputs given while running the bash script

            ./hello.sh aloo gobi bengan kheera

            #output
            aloo gobi bengan kheera

            # to print out the length of the array
            echo $#

---

> Script read line by line from file 
https://www.cyberciti.biz/faq/unix-howto-read-line-by-line-from-file/

                input="filepath/"
                while IFS= read -r line
                do
                    echo "$line"
                done < "$input"

---

> Script output via STDOUT & STDERR

- **ls -al gives the stdout if we want to store this stdout to a file**
- **ls +al is the stderr**

            ls -al 1>file1.txt 2>file2.txt
            # this will send the standard output to file1 while std error to file2
            # so for this case file 2 will be empty


            ls +al 1>file1.txt 2>file2.txt
            # in this case file1 will be empty while file2 will show the error log
 
- **Sending only stdout or stderr to a file**

            ls -al >file1.txt # shows stdout
            or
            ls +al >file1.txt # shows stderr

-**Sending both stdout and stderr in single file**

            ls -al >file1.txt 2>&1

---

> Send output of one script to act as input for another script 

- **a pipe is a special file that connects the output of one process to the input of another process.**

- **exporting something from one script to another script**
            // ----hello.sh----
            MESSAGE="Olaaa! How are You?"
            export MESSAGE
            ./secondScript.sh

            // ---create a new secondScript.sh--
            #! /usr/bin/bash
            echo "Message from Hello script is : $MESSAGE"
            // make it executable
            chmod +x secondScript.sh
            // ls -al to double check

            // now run the hello.sh
            bash hello.sh

---

> String Processing 1:06 https://www.youtube.com/watch?v=e7BufAVwDiM
