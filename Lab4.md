### Step 4: Log into ieng6

Command ucse: SSH&lt;space&gt;cs15lfa23...(here rest of my count)&lt;enter&gt;
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/e224b41c-a01c-4667-bdc9-2224a5ad749a)
Because of the permissions I set up earlier, the computer automatically logs into my account after entering the user name.

### Step 5: Clone your fork of the repository from your Github account (using the SSH URL)
Command used: git&lt;space&gt;clone&lt;space&gt;git@github.com:Awu-Lin/lab7.git&lt;enter&gt;
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/cd8676e1-23f9-4426-a148-8d056eaa0926)

### Step 6: Run the tests, demonstrating that they fail
Command used: cd&lt;space&gt;lab7&lt;enter&gt; (enter into the correct directory)\
Command used: bash&lt;space&gt;test.sh&lt;enter&gt;
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/078b5bb6-0ffd-4f5c-96e6-eedc6e0e845c)

### Step 7: Edit the code file ListExamples.java to fix the failing test (as a reminder, the error in the code is just that index1 is used instead of index2 in the final loop in merge)

Command used: vim&lt;space&gt;ListExamples.java&lt;enter&gt; (open the file in vim)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/96c4b568-e200-4c81-94c7-b0aa59855583)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/cae562ce-3591-4ca6-a8a8-7825111071f3)
After that we move the cursor to index1 which needs to be modified and use the following command\
Command used:cindex2&lt;Esc&gt; (change index1 into index2)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/7f5f4325-57fe-4e40-a4f7-51029e714a6b)
Then we save and quit the vim using following command\
Command used: :wq!&lt;enter&gt; (To make sure the save does take place I used! Enforcement)

### Step 8: Run the tests, demonstrating that they now succeed
Command used: bash&lt;space&gt;test.sh&lt;enter&gt; (proform the test again)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/fbaa0924-5ba0-44dd-8870-68ac7c2e060e)

### Step 9: Commit and push the resulting change to your Github account
Command ucsd:git&lt;space&gt;status&lt;enter&gt; (See which files have been modified)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/4285f44f-89ba-4484-bca5-6a9146092592)
Command ucsd: git&lt;space&gt;add&lt;space&gt;.&lt;enter&gt;\
Command ucsd: git&lt;space&gt;commit&lt;space&gt;-m&lt;space&gt;"change&lt;space&gt;from&lt;space&gt;test1&lt;space&gt;to&lt;space&gt;test2"&lt;enter&gt;
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/6773cfbc-b1c7-4834-8891-303a0228f2d1)
The above command added the file to the staging area and tried to commit the changes, but now I need to set up my Git username and email address. \
Command ucsd: git&lt;space&gt;config&lt;space&gt;--global&lt;space&gt;user.email "zil037@ucsd.com"&lt;enter&gt;\
Command ucsd: git&lt;space&gt;config&lt;space&gt;--global&lt;space&gt;user.name "Benson"&lt;enter&gt;\
Command ucsd: git&lt;space&gt;commit&lt;space&gt;-m&lt;space&gt;"change&lt;space&gt;from&lt;space&gt;test1&lt;space&gt;to&lt;space&gt;test2"&lt;enter&gt;
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/5ee38f9f-a560-45ec-ab9d-cd462419ea8e)
The above command sets up my message and adds a comment\
Command used: git&lt;space&gt;push&lt;space&gt;-u&lt;space&gt;origin&lt;space&gt;main
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/272c7842-a7f4-42c5-a3d7-8ab73834d0a4)
Push my changes to github and now I can see my changes in my repository







