# Bash Scripting

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

- Switch case statement

        29:34 timestamp 
        https://www.youtube.com/watch?v=e7BufAVwDiM