Hello future student!

This post will be about my grading script and server


Code:
`
grade="Grade: 0/6 (file not found)"

rm -rf student-submission
git clone $1 student-submission


cd student-submission/


if [[ -f $"ListExamples.java" ]]
    then
    grade="Grade: 1/6 (file exists, but tests do not compile)"

    

    #run tests
    cd ..
    cp -r lib student-submission/
    cp TestListExamples.java student-submission/
    cd student-submission
    javac -cp ".;../lib/hamcrest-core-1.3.jar;../lib/junit-4.13.2.jar" *.java


    if [[ $? -ne 0 ]] # if the exit code is not 0 for the tests
        then
        echo $grade
        exit 2
    
    else
        grade="Grade: 2/6 (tests compile but don't pass)"
        
    fi

    rm -rf file2.txt
    java -cp ".;../lib/junit-4.13.2.jar;../lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples > file2.txt

    if [[ $? -ne 0 ]] # if the exit code is not 0 for the tests
        then

        echo $grade
        echo `cat file2.txt | grep "There w"`
        echo `cat file2.txt | grep "1)"`
        echo `cat file2.txt | grep "2)"`
        echo `cat file2.txt | grep "Tests run:"`
        exit 3
    
    else
        
        #RESULT=cat file2.txt
        echo "Grade: 6/6 (all tests pass). Output: "
        echo `cat file2.txt | grep "OK"`
        exit 0
        
        
    fi
    
else
    echo $grade
    exit 1
fi

echo $grade
`





![GradeServer](./gradeserver%20lab3.png)

![GradeServer](./gradeserver%20corrected.png)

![GradeServer](./gradeserver%20filename.png)






Tracing the top screenshot (for the lab3 version)

Part 1: setup. All exit codes are irrelevant, and no relevant output/err unless noted

`grade="Grade: 0/6 (file not found)"`

variable assignment

`rm -rf student-submission`

`git clone $1 student-submission`

deletes the old clone directory, and creates a new one. The second line has output
"Cloning into 'student-submission'..."  which is shown on the screen


`cd student-submission/`

Moves into the new directory


Part 2: is the file found?

`if [[ -f $"ListExamples.java" ]]`

For this run though, the ListExamples file is not found (-f is not true, and no file or directory by the name exists)



Part 3: everything that does not run because of the initial if failure

`grade="Grade: 1/6 (file exists, but tests do not compile)"`

reassignment
    

`cd ..`

goes home

`cp -r lib student-submission/`

recursive copy of the lib files for junit into the folder

`cp TestListExamples.java student-submission/`

copies the tests into the folder

`cd student-submission`

moves back

`javac -cp ".;../lib/hamcrest-core-1.3.jar;../lib/junit-4.13.2.jar" *.java`

compiles (this was horrible to figure out)


`if [[ $? -ne 0 ]] # if the exit code is not 0 for the tests`
    `then`
    `echo $grade`
    `exit 2`

this branch runs if the tests fail to pass (if exit code is not 0 for pass)


`else`
    `grade="Grade: 2/6 (tests compile but don't pass)"`
        
`fi`


`rm -rf file2.txt`

`java -cp ".;../lib/junit-4.13.2.jar;../lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples > file2.txt`

Runs junit and copies output to file2.txt



`if [[ $? -ne 0 ]] # if the exit code is not 0 for the tests`
    `then`

    `
    echo $grade
    echo `cat file2.txt | grep "There w"`
    echo `cat file2.txt | grep "1)"`
    echo `cat file2.txt | grep "2)"`
    echo `cat file2.txt | grep "Tests run:"`
    exit 3
    `

    prints out some of the error lines and exits for fail
    
`else`
        
    `
    echo "Grade: 6/6 (all tests pass). Output: "
    echo `cat file2.txt | grep "OK"`
    exit 0
    `

    print out ok and exits for fail
        
        
`fi`



Part 4: the else branch that does run

`else`
    `echo $grade`
    `exit 1`
`fi`

This echoes the original grade statement ("Grade: 0/6 (file not found)") and then exits.



Part 5: last statement

`echo $grade`

This does not run because the else branch exits with code 1. In fact, this code will never run (changes made in the code made it unreachable and I forgot to delete it)




Return codes end up being irrelevant for the entire script (however, the exit codes of the statements javac -cp ".;../lib/hamcrest-core-1.3.jar;../lib/junit-4.13.2.jar" *.java or java -cp ".;../lib/junit-4.13.2.jar;../lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples > file2.txt)
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
Hope this helped enough!




