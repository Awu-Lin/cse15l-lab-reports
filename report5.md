## Part 1 - Debugging Scenario
### Student 
Hello, everyone! I'm currently practicing using a bash script to unify my Junit tests, but I'm having some very strange problems running the script, I'm sure I've put the hamcrest-core and Junit files in the right place but after I run my script it shows the following result
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/8f425810-1c3b-49ba-89ef-cf6296666b12)\
Currently my catalog is formatted like this and I don't think it should have any problems. Can anyone help me please?
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/cfa3f6e3-6615-4ea4-9935-2cca74f43075)\
Oh, and here is my bash script.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/fca8cb00-a98d-43d7-b856-feaa3792083f)



### TA
Hey, thank you for your quetion! And I suggest you pay attention to what your script is executing as a command. Think about what it should ideally be doing and then check for errors in the script.

### Student 
Thank you for your response! I rechecked my script and realized that I was using the wrong class path format, after correcting it my script works fine, it now looks like the following picture
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/0882dc69-34ba-496a-9cb2-b73a61583494)\
But even so, in the course of running my tests I realized that I was getting an unthinkable result for my test 4. My code was trying to average a set of numbers, and I was getting the following error when dealing with the case of very large numbers being added together
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/b2c59c7a-180a-4ce1-ac76-c44f55b84e15)\
My test is as follows, and I can't for the life of me figure out why it's getting a negative number
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/e3bd72fb-a34c-4f54-867e-849742959d60)\
Here is my completed code
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/446c43bd-0c8c-42f9-be38-5d43866d7239)\

### TA
I'd be happy to help you with this question; the choice of data type is critical when dealing with calculations involving very large or very small values. You have already worked with the int type, and I suggest that you think about the differences between it and the other base data types as well as the characteristics that the int type itself has and the significance of this difference when dealing with computational problems.

### Student 
Ohhhhh I see! I was using the int type so it would overflow due to storage overload when dealing with values close to Integer.MAX_VALUE, I've corrected my code to use the long type instead of int and now all my tests pass. Thanks for your help!
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/fa0fbdac-15ee-4835-948d-38b9d816061a)\

### TA
great work!

## Summary for step 4: The file & directory structure needed
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/55d84ed9-6312-499a-bca0-b9a3e90ba9b5)

It contains a main folder called "Lab 5". Inside this main folder, there is a subfolder called "lib" and several files. The "lib" folder contains two JAR files: hamcrest-core-1.3.jar and junit-4.12.jar, which are Java libraries commonly used for unit testing. There are also two Java source files in the "Lab 5" folder: MathOperations.java and MathOperationsTest.java, which represent a class and its test class, respectively. There is also a script file called run_tests.sh, which is the shell script used to run the tests

### The contents of each file before fixing the bug
MathOperations (This code is the main code of the average program)
``` java
public class MathOperations {
    public static double calculateAverage(int[] numbers) {
        if (numbers == null || numbers.length == 0) {
            throw new IllegalArgumentException("Array is empty or null");
        }

        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        return sum / numbers.length; 
    }
}
```

MathOperationsTest (It contains four tests, test 4 will cause a data overflow, which is a bug in the program)
``` java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class MathOperationsTest {

    @Test
    public void testCalculate1() {
        int[] numbers = { 1, 2, 3, 4, 5 };
        double result = MathOperations.calculateAverage(numbers);
        assertEquals("Average calculation should be correct", 3.0, result, 0.001);
    }

    @Test(expected = IllegalArgumentException.class)
    public void testCalculate2() {
        int[] numbers = {};
        MathOperations.calculateAverage(numbers);
    }

    @Test
    public void testCalculate3() {
        int[] numbers = {-3, -2, 2, 3};
        double result = MathOperations.calculateAverage(numbers);
        assertEquals("Average calculation should be correct", 0.0, result, 0.001);
    }

    @Test
    public void testCalculate4() {
        int[] numbers = {Integer.MAX_VALUE, Integer.MAX_VALUE, -2};
        double result = MathOperations.calculateAverage(numbers);
        assertEquals("Average calculation should account for integer overflow", 
        (double)(Integer.MAX_VALUE - 1), result, 0.001);
    }
}
```

run_tests.sh (A script that uses the wrong format of the windos command which causes the error in the first place)
```java
#!/bin/bash
javac MathOperations.java
java MathOperations
javac -cp .:junit-4.12.jar MathOperationsTest.java
java -cp .:junit-4.12.jar org.junit.runner.JUnitCore MathOperationsTest
```

### The full command line (or lines) you ran to trigger the bug
The first bug is caused by the
```java
Java MathOperations
``` 
The second bug is caused by the 
```java
int sum = 0;
```

### A description of what to edit to fix the bug
For the first error, the student corrected the correct script instruction format, removed the `Java MathOperations` instruction, and let the script run again. For the second error, the student used the long type instead of the int type to prevent data overflow and solve the problem

## Part 2
In the second half of this semester's experimental class, I gained a profound understanding of two specific fields: Bash scripting and Vim editors. Prior to this, my understanding of Bash scripts was very limited. I learned about the power and efficiency it brings when automating tasks in a Linux environment, which broadened my horizons and was extremely practical. These knowledge have simplified my workflow, especially when managing files and performing repetitive tasks, opening up new possibilities for me. What surprised me was that I didn't have to type commands one by one on the terminal, which saved me a lot of time!\
Similarly, my experience with Vim was also disruptive. Before taking this course, I only saw Vim as another text editor, just like I needed to download a platform like vscode, but later I discovered its powerful features. The modal characteristics of Vim, as well as its various modes for editing, insertion, and navigation, are a novel concept for me. I have learned many shortcut keys and commands, which have greatly improved my coding and text editing efficiency. Exploring Vim is not just about learning a tool, but also adopting a more thoughtful and efficient coding method. I can directly access files without actually opening them, and I can also make changes and save them. This is also very cool.





