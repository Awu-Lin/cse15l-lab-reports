## Part 1 - Debugging Scenario
### Student 
Hello, everyone! I'm currently practicing using a bash script to unify my Junit tests, but I'm having some very strange problems running the script, I'm sure I've put the hamcrest-core and Junit files in the right place but after I run my script it shows the following result
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/d55d0a7a-80f9-4866-921a-647999b26fa0)\
Currently my catalog is formatted like this and I don't think it should have any problems. Can anyone help me please?\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/b2f6f229-666f-494e-bb29-60d990825b16)\
and here is my bash script.\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/5d1a6a5e-912f-4423-ae97-48b6f03393be)




### TA
Hey, thank you for your quetion! And I suggest you pay attention to what your script is executing as a command. Pay special attention to the path names you use and the syntax is correct. 

### Student 
Thank you for your response! I rechecked my script and realized that I was using the wrong class path format, after correcting it my script works fine, it now looks like the following picture
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/45b17d44-fb9f-41f5-b13b-ef71b9498684)\
But even so, in the course of running the test, I realized that I was getting an unimaginable result when I entered the value -2147483412. My code is trying to invert an array so that for example it should output 123 when the input value is 321 and -123 when the input is -321, and now I'm getting the error in the following image
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/4fe8b57e-8bb6-4846-9d79-11d33a66e77d)\
What's also strange is that my test passed when dealing with overflow, so I'm wondering why this test is now giving me an error cause 2147483412 is acturallly in the range of int.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/95d693c7-c7f3-416c-a976-e59d085a78d4)
Here is my completed code\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/64b98f58-7d66-4088-8fed-ea2340863911)


### TA
I'd be happy to help you with this question; I see that you've added an overflow check to the data to prevent it from overflowing, which is great, but you need to pay attention to the logic of the code when doing the overflow check, and especially think about what it should look like in conjunction with the parts of the code you've already done before. As a suggestion, you can break down each step of the code run and pay attention to the changes in the numbers that occur during those runs.

### Student 
Ohhhhh I got it! The problem occurs when count becomes 214748341, and the next step is to multiply it by 10 and add the next number, 2. However, 2147483410 + 2 equals 2147483412, which exceeds Integer.MAX_VALUE, so it will return 0; I fixed the logic of my code to have it check for an overflow before the number is multiplied by 10 and added to the next number Instead of after, it checks to see if it will overflow, and now my test passes successfully. Thank you for your help!
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/8ee89079-34c6-432c-9c55-ff8e2b63d2d2)

### TA
great work!

## Summary for step 4: The file & directory structure needed
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/b0885b5e-3a35-4674-820b-c767c71b2f52)

It contains a main folder called "Lab 5". Inside this main folder, there is a subfolder called "lib" and several files. The "lib" folder contains two JAR files: hamcrest-core-1.3.jar and junit-4.12.jar, which are Java libraries commonly used for unit testing. There are also two Java source files in the "Lab 5" folder: Solution.java and SolutionTest.java, which represent a class and its test class, respectively. There is also a script file called run_tests.sh, which is the shell script used to run the tests

### The contents of each file before fixing the bug
Solution.java (This code is the main code of the reverse program, for example, input 321 will have output 123 and -321 will result in -123)
``` java
publclass Solution {
    public int reverse(int x) {
        int count = 0;
        int temp = Math.abs(x);
        while(temp>0){
            int number = temp%10;
            temp = temp/10;
            count = count*10+ number;

            if (count > (Integer.MAX_VALUE - number) / 10) {
                return 0;
            }
        }

    if (x < 0) {
        count = -count;
    }
    
    return count;
    }
}
```

SolutionTest.java (It contains 6 tests, test `testReverseNegative2147483412` will cause a problem in program)
``` java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testNormalCase() {
        Solution solution = new Solution();
        assertEquals(321, solution.reverse(123));
    }

    @Test
    public void testZero() {
        Solution solution = new Solution();
        assertEquals(0, solution.reverse(0));
    }

    @Test
    public void testNegativeNumber() {
        Solution solution = new Solution();
        assertEquals(-321, solution.reverse(-123));
    }

    @Test
    public void testOverflow() {
        Solution solution = new Solution();
        assertEquals(0, solution.reverse(1000000009)); // This number will overflow when reversed
    }

    @Test
    public void testBoundaryCondition() {
        Solution solution = new Solution();
        assertEquals(0, solution.reverse(Integer.MAX_VALUE)); // Test the reverse of max int
        assertEquals(0, solution.reverse(Integer.MIN_VALUE)); // Test the reverse of min int
    }

    @Test
    public void testReverseNegative2147483412() {
        Solution solution = new Solution();
        // The expected result is based on reversing the digits of -2147483412.
        // However, since reversing it will not cause an overflow, it should return the reversed number.
        // Reversed number should be -2143847412.
        int expected = -2143847412;
        assertEquals(expected, solution.reverse(-2147483412));
    }
}


```

run_tests.sh (A script that uses the wrong format of the windos command which causes the error in the first place)
```java
#!/bin/bash
javac -cp .;libjunit-4.12.jar Solution.java SolutionTest.java
java -cp .;libjunit-4.12.jar org.junit.runner.JUnitCore SolutionTest
```

### The full command line (or lines) you ran to trigger the bug
The first bug is caused by the
```java
javac -cp .;libjunit-4.12.jar Solution.java SolutionTest.java
java -cp .;libjunit-4.12.jar org.junit.runner.JUnitCore SolutionTest
``` 
The second bug is caused by the 
```java
while(temp>0){
    int number = temp%10;
    temp = temp/10;
    count = count*10+ number;

    if (count > (Integer.MAX_VALUE - number) / 10) {
        return 0;
    }
```

### A description of what to edit to fix the bug
For the first error, the student corrected the correct formatting of the script instructions, and after using the correct references to the source and the correct symbols the student ran the script again and passed the run with flying colors. For the second error, the student's overflow protection logic was not refined enough. After correcting the overflow protection logic, the overflow test will occur before the count is multiplied by 10 and the next number is added, rather than after processing, thus avoiding an unnecessary overflow error judgment.

The first bug is fixed to
```java
#!/bin/bash
javac -cp .:lib/* Solution.java SolutionTest.java
java -cp .:lib/* org.junit.runner.JUnitCore SolutionTest
```

The second bug is fixed to
```java
while(temp > 0){
    int number = temp % 10;
    temp = temp / 10;
    if (count > Integer.MAX_VALUE / 10 || (count == Integer.MAX_VALUE / 10 && number > 7))         {
        return 0;
        }
    count = count * 10 + number;
}
```
## Part 2
In the second half of this semester's experimental class, I gained a profound understanding of two specific fields: Bash scripting and Vim editors. Prior to this, my understanding of Bash scripts was very limited. I learned about the power and efficiency it brings when automating tasks in a Linux environment, which broadened my horizons and was extremely practical. These knowledge have simplified my workflow, especially when managing files and performing repetitive tasks, opening up new possibilities for me. What surprised me was that I didn't have to type commands one by one on the terminal, which saved me a lot of time!\
Similarly, my experience with Vim was also disruptive. Before taking this course, I only saw Vim as another text editor, just like I needed to download a platform like vscode, but later I discovered its powerful features. The modal characteristics of Vim, as well as its various modes for editing, insertion, and navigation, are a novel concept for me. I have learned many shortcut keys and commands, which have greatly improved my coding and text editing efficiency. Exploring Vim is not just about learning a tool, but also adopting a more thoughtful and efficient coding method. I can directly access files without actually opening them, and I can also make changes and save them. This is also very cool.





