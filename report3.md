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
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/95a14240-8bb4-438b-bd71-a07a1b7b00bf)

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
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/8a1c78dd-ff13-42d4-8f24-af2e152e41ed)

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
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/376aeb4b-1c2b-4072-abcc-75db0c9483e7)

## Briefly describe why the fix addresses the issue.
Before Fixed, the loop did not retain the replaced values when replacing elements, which resulted in some elements being permanently overwritten before the middle of the array. Specifically, when the loop reached the middle element of the array, the second half of the elements were lost before they were replaced.

The fixed code uses a temporary variable temp to hold the value of the replaced element, which ensures that the value is not lost before moving an element to its final position. The loop only goes halfway through the array because all swapping is done when processing reaches the midpoint. Each step exchanges elements in two positions, one from the front of the array and the other from the back of the array.

### Part 2
## 1.-type option
This option is used to search by file type. It can be f for normal files, d for directories, etc.

Example 1: Searching the . /technical directory.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/c4d65cc2-4429-408e-8d7a-9dc6b4de2541)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/c520ea30-6215-4b5d-8703-a3e0211473ca)

Example 2: Find all directories in the . /technical directory
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/98b8630f-1cef-472a-8984-57efe3d9be43)\
This command finds all directories in the . /technical directory and all directories under its subdirectories. This is very useful when I need to perform an operation on a directory.

## 2. -name option
The -name option is used to search by file name.

Example 1: Find all files ending in .txt.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/7b0580b3-e81b-41bd-ae42-3ec0539c8f43)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/89392ed7-62b3-4943-ad0d-05b5ff2a543d)\
This command finds all files ending in .txt. This is very useful when searching for specific types of files. (Although there are too many txt files in this document)

Example 2: Find all files starting with specific character in the . /technical directory.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/47fe482c-cf0e-4c40-a8fc-ab9787fa660d)\
This command looks for all files that begin with a specific character (chapter in the example).

## 3. -size option
The -size option is used to search by file size.

Example 1: Finding files over 150KB in the . /technical directory that is larger than 50KB.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/8b5cc1ce-e9d3-400d-bc40-001a2f724b0c)\
This command is used to find files larger than 150KB, very useful for disk cleanup or find large files for analysis.

Example 2: Finding files less than 1MB in the . /technical directory for files less than 1MB in size.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/c244825d-49b3-4af5-a7c1-22acccea1827)\
This command is used to find files that are less than 1MB in size, which helps to identify smaller files.

## 4. -exec option
The -exec option allows commands to be executed for each file found.

Example 1: Delete rr37.txt file in the /technical directory.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/0c73bfd7-579c-4a60-8529-0ec463370168)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/5e5f6bfd-4efd-47c1-948b-f2ff16163f1f)\
This command looks for files ending with rr37.txt and deletes it. This is useful when cleaning up temporary files.

Example 2: Find all og files in the . /technical directory and append its contents to a master log file.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/71ca3e64-67a2-46b5-8e46-ba0f813dc933)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/8de9e8e7-bdfd-4178-be34-d3594a4686e6)\
This command combines the contents of all og files found into one file, which is useful for log management.



