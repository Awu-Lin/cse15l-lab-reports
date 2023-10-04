1. `cd` with no arguments:
     The `cd` command with no arguments will take the user to their home directory.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/6dd14a2a-6619-41fa-8efe-143961fa8a65)\
**Working Directory:** /home.\
**Explanation:** When don't provide any argument to the `cd` command, it will take to the home directory, which is usually `/home/username` for Unix systems.\
**Output:** Not an error.

2. `cd` with a path to a directory as an argument:
     Let's say you want to change to the `lecture1` directory.
   ![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/d7f444c9-6987-44f2-95f7-a4ac926be37d)\
   **Working Directory:** /home/Lecture1.\
   **Explanation:** The `cd` command takes to the `lecture1` directory.\
   **Output:** Not an error.
   
3. `cd` with a path to a file as an argument:
   Trying to change to a file.
   ![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/4e716873-1785-47ed-86e1-7c6a857bd5b9)\
   **Working Directory:** Anywhere in the filesystem cause it is an Error.\
   **Explanation:** We cannot use `cd` with a file.\
   **Output:** Error, because `Hello.java` is a file, not a directory.

4. `ls` with no arguments:
     Lists the contents of the current directory.\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/c1677ff6-cfc0-44d1-9c90-bf4be7b7f5d8)\
**Working Directory:** /home.\
**Explanation:** `ls` displays all the files and directories in the current directory.\
**Output:** Not an Error

5. `ls` with a path to a directory as an argument:
     Same with `cd`, see lecture1 as an example\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/59ac3837-365f-44d8-befa-bf49fb939b8a)\
**Working Directory:** /home.\
**Explanation:** `ls` displays all the files and directories in the target directory, lecture1 in example\
**Output:** Not an Error

6. `ls` with a path to a file as an argument:
   see Hello.java as an example\
   ![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/0f4f3bbc-da30-4eb4-94d1-698518b36884)\
   **Working Directory:** /home/lecture1.\
   **Explanation:** `ls` displays the file name.\
   **Output:** Not an Error

7. `cat` with a path to a file as an argument:
   Without arguments, cat will going to expects input from the standard input.\
   ![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/76240d08-1df9-4899-a099-f247484e4c69)\
   **Working Directory:** Anywhere in the filesystem cause it waiting for enter\
   **Explanation:** `cat` will wait for input.\
   **Output:** Not an Error, but it will always awaits.

8. `cat` with a path to a directory as an argument:
     Same with `cd` and, see lecture1 as an example\
     ![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/396089a6-b021-4fd9-8d5f-18d3cd616d81)\
     **Working Directory:** Anywhere in the filesystem cause it is an Error.\
     **Explanation:** cannot use `cat` on a directory.\
     **Output:** Error

9. `cat` with a path to a file as an argument:
   see Hello.java as an example\
   ![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/5a2a23cf-eb9e-479f-b959-0291897f8353)\
   **Working Directory:** /home/lecture1.\
   **Explanation:** `cat` displays the contents of the Hello.java file.\
   **Output:** Not an Error





