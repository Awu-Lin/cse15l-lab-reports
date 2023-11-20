### Part 1
## 1. A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

This JUnit test checks if the `reverseInPlace` method from `ArrayExamples` correctly reverses an array in place.

```java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class ArrayExamplesTest {
    @Test
    public void testReverseInPlace() {
        int[] originalArray = { 1, 2, 3, 4, 5 };
        int[] expectedReversed = { 5, 4, 3, 2, 1 };

        ArrayExamples.reverseInPlace(originalArray);
        assertArrayEquals("It should be reversed in place", expectedReversed, originalArray);
    }
}

```
Here is out put
```java
JUnit version 4.13.2
..E
Time: 0.007
There was 1 failure:
1) testReverseInPlace(ArrayExamplesTest)
The array should be reversed in place: arrays first differed at element [3]; expected:<2> but was:<4>
    at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
    at org.junit.Assert.internalArrayEquals(Assert.java:534)
    at org.junit.Assert.assertArrayEquals(Assert.java:418)
    at ArrayExamplesTest.testReverseInPlace(ArrayExamplesTest.java:13)
    ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<2> but was:<4>
    at org.junit.Assert.fail(Assert.java:89)
    at org.junit.Assert.failNotEquals(Assert.java:835)
    at org.junit.Assert.assertEquals(Assert.java:120)
    at org.junit.Assert.assertEquals(Assert.java:146)
    at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
    at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
    ... 35 more

FAILURES!!!
Tests run: 3, Failures: 1
```

## 2. An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```java
import org.junit.Assert;
import org.junit.Test;

public class TestWithoutBug {
    @Test
    public void testReverseInPlaceWithSingleElement() {
        int[] originalArray = { 1 };
        int[] expectedArray = { 1 };

        ArrayExamples.reverseInPlace(originalArray);

        Assert.assertArrayEquals("An array with a single element should remain unchanged when reversed in place",
                expectedArray, originalArray);
    }
}
```
Here is out put
```java
PS C:\Users\22697\Desktop\15\lab3-main\lab3> javac -cp ".;lib/*" TestWithoutBug.java
PS C:\Users\22697\Desktop\15\lab3-main\lab3> java -cp ".;lib/*" org.junit.runner.JUnitCore TestWithoutBug

JUnit version 4.13.2
.
Time: 0.006

OK (1 test)
```

## 3. The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

Before 

```java
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
After 
```java
static void reverseInPlace(int[] arr) {
        int temp;
        for (int i = 0; i < arr.length / 2; i++) {
            temp = arr[i];
            arr[i] = arr[arr.length - i - 1];
            arr[arr.length - i - 1] = temp;
        }
}
```
After completing the corrections the test passed successfully
```java
PS C:\Users\22697\Desktop\15\lab3-main\lab3> javac -cp ".;lib/*" ArrayExamplesTest.java
PS C:\Users\22697\Desktop\15\lab3-main\lab3> java -cp ".;lib/*" org.junit.runner.JUnitCore ArrayExamplesTest

JUnit version 4.13.2
...
Time: 0.007

OK (3 tests)
```

## Briefly describe why the fix addresses the issue.
Before Fixed, the loop did not retain the replaced values when replacing elements, which resulted in some elements being permanently overwritten before the middle of the array. Specifically, when the loop reached the middle element of the array, the second half of the elements were lost before they were replaced.

The fixed code uses a temporary variable temp to hold the value of the replaced element, which ensures that the value is not lost before moving an element to its final position. The loop only goes halfway through the array because all swapping is done when processing reaches the midpoint. Each step exchanges elements in two positions, one from the front of the array and the other from the back of the array.

### Part 2
## 1.-type option
This option is used to search by file type. It can be f for normal files, d for directories, etc.

Example 1: Searching the . /technical directory.
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/lab3
$ find ./technical -type f
```
```plaintext
./technical/biomed/1471-2350-2-2.txt
./technical/biomed/1471-2350-2-8.txt
./technical/biomed/1471-2350-3-1.txt
./technical/biomed/1471-2350-3-12.txt
./technical/biomed/1471-2350-3-7.txt
./technical/biomed/1471-2350-3-9.txt
./technical/biomed/1471-2350-4-2.txt
./technical/biomed/1471-2350-4-3.txt
./technical/biomed/1471-2350-4-4.txt
./technical/biomed/1471-2350-4-6.txt
./technical/biomed/1471-2369-3-1.txt
./technical/biomed/1471-2369-3-10.txt
./technical/biomed/1471-2369-3-6.txt
./technical/biomed/1471-2369-3-9.txt
./technical/biomed/1471-2369-4-1.txt
./technical/biomed/1471-2369-4-5.txt
./technical/biomed/1471-2377-1-2.txt
./technical/biomed/1471-2377-2-4.txt
./technical/biomed/1471-2377-2-6.txt
./technical/biomed/1471-2377-3-4.txt
./technical/biomed/1471-2407-1-13.txt
./technical/biomed/1471-2407-1-15.txt
./technical/biomed/1471-2407-1-19.txt
./technical/biomed/1471-2407-1-6.txt
./technical/biomed/1471-2407-2-11.txt
./technical/biomed/1471-2407-2-12.txt
./technical/biomed/1471-2407-2-15.txt
./technical/biomed/1471-2407-2-16.txt
./technical/biomed/1471-2407-2-17.txt
./technical/biomed/1471-2407-2-18.txt
./technical/biomed/1471-2407-2-19.txt
./technical/biomed/1471-2407-2-22.txt
./technical/biomed/1471-2407-2-23.txt
```

Example 2: Find all directories in the . /technical directory
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/docsearch (main)
$ find ./technical -type d
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
This command finds all directories in the . /technical directory and all directories under its subdirectories. This is very useful when I need to perform an operation on a directory.

## 2. -name option
The -name option is used to search by file name.

Example 1: Find all files ending in .txt.
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/docsearch (main)
$ find ./technical -name "*.txt"
```
```plaintext
./technical/biomed/1471-2334-1-24.txt
./technical/biomed/1471-2334-1-9.txt
./technical/biomed/1471-2334-2-1.txt
./technical/biomed/1471-2334-2-24.txt
./technical/biomed/1471-2334-2-26.txt
./technical/biomed/1471-2334-2-27.txt
./technical/biomed/1471-2334-2-29.txt
./technical/biomed/1471-2334-2-5.txt
./technical/biomed/1471-2334-2-6.txt
./technical/biomed/1471-2334-2-7.txt
./technical/biomed/1471-2334-3-10.txt
./technical/biomed/1471-2334-3-11.txt
./technical/biomed/1471-2334-3-12.txt
./technical/biomed/1471-2334-3-13.txt
./technical/biomed/1471-2334-3-15.txt
./technical/biomed/1471-2334-3-9.txt
./technical/biomed/1471-2350-2-11.txt
./technical/biomed/1471-2350-2-12.txt
./technical/biomed/1471-2350-2-2.txt
./technical/biomed/1471-2350-2-8.txt
./technical/biomed/1471-2350-3-1.txt
./technical/biomed/1471-2350-3-12.txt
./technical/biomed/1471-2350-3-7.txt
./technical/biomed/1471-2350-3-9.txt
./technical/biomed/1471-2350-4-2.txt
./technical/biomed/1471-2350-4-3.txt
./technical/biomed/1471-2350-4-4.txt
./technical/biomed/1471-2350-4-6.txt
./technical/biomed/1471-2369-3-1.txt
./technical/biomed/1471-2369-3-10.txt
./technical/biomed/1471-2369-3-6.txt
```
This command finds all files ending in .txt. This is very useful when searching for specific types of files. (Although there are too many txt files in this document)

Example 2: Find all files starting with specific character in the . /technical directory.
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/docsearch (main)
$ find ./technical -type d
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
This command looks for all files that begin with a specific character (chapter in the example).

## 3. -size option
The -size option is used to search by file size.

Example 1: Finding files over 150KB in the . /technical directory that is larger than 50KB.
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/docsearch (main)
$ find ./technical -size +150k
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-3.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/About_LSC/State_Planning_Report.txt
./technical/government/Env_Prot_Agen/bill.txt
./technical/government/Env_Prot_Agen/multi120902.txt
./technical/government/Env_Prot_Agen/tech_adden.txt
./technical/government/Gen_Account_Office/d01591sp.txt
./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./technical/government/Gen_Account_Office/pe1019.txt
./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
```
This command is used to find files larger than 150KB, very useful for disk cleanup or find large files for analysis.

Example 2: Finding files less than 1MB in the . /technical directory for files less than 1MB in size.
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/docsearch (main)
$ find ./technical -size -1M
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
This command is used to find files that are less than 1MB in size, which helps to identify smaller files.

## 4. -exec option
The -exec option allows commands to be executed for each file found.

Example 1: Delete rr37.txt file in the /technical directory.
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/docsearch (main)
$ find ./technical -type f -name "og*" -exec cat {} \; >> all_logs.txt
```
```markdown
rr73.txt
rr74.txt
rr166.txt
rr167.txt
rr171.txt
rr172.txt
rr191.txt
rr196.txt
```
This command looks for files ending with rr37.txt and deletes it. This is useful when cleaning up temporary files.

Example 2: Find all og files in the . /technical directory and append its contents to a master log file.
```shell
22697@Benson MINGW64 ~/Desktop/15/lab3-main/docsearch (main)
$ find ./technical -type f -name "og*" -exec cat {} \; >> all_logs.txt
```

对于第二张图片，它显示了文件内容的一部分，以下是这部分内容的文本表示：

```markdown
B-271810
April 26, 1996
The Honorable John H. Chafee Chairman The Honorable Max Baucus
Ranking Minority Member Committee on Environment and Public Works
United States Senate
The Honorable Thomas J. Bliley, Jr. Chairman The Honorable John
D. Dingell Ranking Minority Member Committee on Commerce House of
Representatives
Subject: Revision of Fee Schedules; 100% Fee Recovery, FY
1966
Pursuant to section 801(a)(2)(A) of title 5, United States Code,
this is our report on a major rule promulgated by the Nuclear
Regulatory Commission entitled "Revision of Fee Schedules; 100% Fee
Recovery, FY 1966" (RIN 3150-AF39). The rule implements for fiscal
year 1966 section 6101 of the Omnibus Budget Reconciliation Act of
1990, as amended, 42 U.S.C. § 2214, which requires the Commission
to recover from its applicants and licensees approximately 100
percent of its budget authority less amounts appropriated from the
Nuclear Waste Fund. It was published in the Federal Register as a
final rule on April 12, 1996. 61 Fed. Reg. 16203.
Enclosed is our assessment of the Commission's compliance with
the procedural steps required by section 801(a)(1)(B)(i) through
(iv) of title 5 with respect to the rule. Our review indicates that
the Commission complied with the applicable requirements.
GAO/OGC-96-9
If you have questions concerning the substance of the rule,
please contact Victor S. Rezendes, Director for Energy, Resources,
and Science Issues, on 512-3841.
Sincerely yours,
```
This command combines the contents of all og files found into one file, which is useful for log management.





