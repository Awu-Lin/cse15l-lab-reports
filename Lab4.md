### Step 4: Log into ieng6

Command ucse: SSH`<space>`cs15lfa23...(rest of my count information)`<enter>`
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/e224b41c-a01c-4667-bdc9-2224a5ad749a)
Because of the permissions I set up earlier, the computer automatically logs into my account after entering the user name.

### Step 5: Clone your fork of the repository from your Github account (using the SSH URL)
Command ucsd: `<Ctrl-C>`(This step happens outside of the terminal and I copied the "git@github.com:Awu-Lin/lab7.git" link that needs to be cloned)\
Command used: git`<space>`clone`<space>` `<Ctrl-V>` `<enter>` (Paste the already cloned "git@github.com:Awu-Lin/lab7.git" link)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/cd8676e1-23f9-4426-a148-8d056eaa0926)

### Step 6: Run the tests, demonstrating that they fail
Command used: cd`<space>`lab7`<enter>` (enter into the correct directory)\
Command used: bash`<space>`test.sh`<enter>`
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/078b5bb6-0ffd-4f5c-96e6-eedc6e0e845c)

### Step 7: Edit the code file ListExamples.java to fix the failing test (as a reminder, the error in the code is just that index1 is used instead of index2 in the final loop in merge)

Command used: vim`<space>`ListExamples.java`<enter>` (open the file in vim)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/96c4b568-e200-4c81-94c7-b0aa59855583)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/cae562ce-3591-4ca6-a8a8-7825111071f3)
After that we move the cursor to index1 which needs to be modified and use the following command\
Command used:cindex2`<Esc>` (change index1 into index2)\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/7f5f4325-57fe-4e40-a4f7-51029e714a6b)
Then we save and quit the vim using following command\
Command used: :wq!`<enter>` (To make sure the save does take place I used! Enforcement)\

### Step 8: Run the tests, demonstrating that they now succeed
Command used: `<up>` `<up>` (Rerunning the `bash test.sh` command, this is the third command in the terminal's history, so I  `<up>` twice to find it)\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/fbaa0924-5ba0-44dd-8870-68ac7c2e060e)

### Step 9: Commit and push the resulting change to your Github account
Command ucsd:git`<space>`status`<enter>` (See which files have been modified)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/4285f44f-89ba-4484-bca5-6a9146092592)
Command ucsd: git`<space>`add`<space>`.`<enter>`\
Command ucsd: git`<space>`commit`<space>`-m`<space>`"change`<space>`from`<space>`test1`<space>`to`<space>`test2"`<enter>`
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/6773cfbc-b1c7-4834-8891-303a0228f2d1)
The above command added the file to the staging area and tried to commit the changes, but now I need to set up my Git username and email address. \
Command ucsd: git`<space>`config`<space>`--global`<space>`user.email "zil037@ucsd.com"`<enter>`\
Command ucsd: `<up>` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` `delete` (23 delete instructions).name`<space>`"Benson"`<enter>` (Use `<up>`  to go back to `git config --global user.email "zil037@ucsd.com"` and `delete` the information in it until It have `git config --global user` remaining, then add `.name "Benson"` after it, and finally run) \
Command ucsd: `<up>` `<up>` `<up>` `<enter>` (Rerun the `git commit -m "change from test1 to test2"` command, it's in the eighth position of the record so use the three `<up>` commands to find it)\
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/5ee38f9f-a560-45ec-ab9d-cd462419ea8e)
The above command sets up my message and adds a comment\
Command used: git`<space>`push`<space>`-u`<space>`origin`<space>`main
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/272c7842-a7f4-42c5-a3d7-8ab73834d0a4)
Push my changes to github and now I can see my changes in my repository







