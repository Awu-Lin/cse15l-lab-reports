## Part 1 - Debugging Scenario
### Student 
Hello, everyone! I'm currently practicing using a bash script to unify my Junit tests, but I'm having some very strange problems running the script, I'm sure I've put the hamcrest-core and Junit files in the right place but after I run my script it shows the following result
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/8f425810-1c3b-49ba-89ef-cf6296666b12)
Currently my catalog is formatted like this and I don't think it should have any problems. Can anyone help me please?
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/cfa3f6e3-6615-4ea4-9935-2cca74f43075)\
Oh, and here is my bash script.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/53794b42-06f8-41c1-af04-3213a1dc55ef)


### TA
Hey, thank you for your quetion! And I suggest you pay attention to what your script is executing as a command. Think about what it should ideally be doing and then check for errors in the script.

### Student 
Thank you for your response! I rechecked my script and realized that I was using the wrong class path format, after correcting it my script works fine, it now looks like the following picture
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/0882dc69-34ba-496a-9cb2-b73a61583494)
But even so, in the course of running my tests I realized that I was getting an unthinkable result for my test 4. My code was trying to average a set of numbers, and I was getting the following error when dealing with the case of very large numbers being added together
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/b2c59c7a-180a-4ce1-ac76-c44f55b84e15)
My test is as follows, and I can't for the life of me figure out why it's getting a negative number


