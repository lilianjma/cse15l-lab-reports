# Streamline ssh Configuration  
*Description: This allows you to create a shortcut for your username instead of having to write out the entire .ucsd.edu account name.*  

1. Show your .ssh/config file, and how you edited it (with VScode, another program, etc)  
<img width="752" alt="Screen Shot 2022-05-05 at 9 35 03 PM" src="https://user-images.githubusercontent.com/31358827/167067700-456b06de-054d-4553-b646-3e9b67abb1c7.png">

2. Show the ssh command logging you into your account using just the alias you chose.  
<img width="717" alt="Screen Shot 2022-05-05 at 9 36 08 PM" src="https://user-images.githubusercontent.com/31358827/167067778-93f4d630-0849-40fe-8d54-99fe8b7378b2.png">

3. Show an scp command copying a file to your account using just the alias you chose.  
<img width="689" alt="Screen Shot 2022-05-06 at 8 04 04 PM" src="https://user-images.githubusercontent.com/31358827/167235550-b8dcfde3-10cd-4024-a4ea-9125ee4e72e8.png">  



# Setup Github Access from ieng6
1. Show where the public key you made is stored on Github and in
your user account (screenshot).
<img width="1440" alt="Screen Shot 2022-05-07 at 9 27 03 AM" src="https://user-images.githubusercontent.com/31358827/167263221-8a0fb885-a4fa-4599-9a2f-f52638e118d4.png">

2. Show where the private key you made is stored on your user
account (but not its contents) as a screenshot.  
<img width="479" alt="Screen Shot 2022-05-07 at 9 28 28 AM" src="https://user-images.githubusercontent.com/31358827/167263277-fcba47f3-b55a-42ad-82ae-0a37b97885c5.png">

3. Show running git commands to commit and push a change to
Github while logged into your ieng6 account.  
<img width="1067" alt="Screen Shot 2022-05-07 at 9 25 07 AM" src="https://user-images.githubusercontent.com/31358827/167263169-66ef790b-28b2-4859-8e04-e8c0e458ae38.png">

4. Show a link for the resulting commit.  
[Link to resulting commit](https://github.com/lilianjma/good-markdown-parser/commit/81853d4679d9decbcd14f64f76f217a0e1c78737)  


### Steps for this section
1. In your ssh, use the command `ssh-keygen`. Press enter for the rest of the prompts.
2. `cat [file path to the id_rsa.pub]` and copy the resultant contents from that. You can also use `pbcopy < [filepath to id_rsa.pub]` to directly copy the contents of the file.
3. In github, create a new SSH key, title it something, then and copy paste into the big text file and save. To create a new ssh key, click on your profile pic, go to settings, then go to *SSH and GPG keys* and you will be able to create a new SSH key from there.
4. Go back to the terminal, and to clone a repository on ur ieng, when you click on code to copy the link to clone it, go to the SSH tab instead of the HTTPS tab to copy the url. Then use `git clone [paste the url]` in your SSH terminal.
5. Go into the cloned repository, and edit it by adding a file using `touch [name of new file]`
6. Commit the change by using `git commit -m "some message here"`
7. Push the commit by using `git push origin main` and you're done.

<img width="1067" alt="Screen Shot 2022-05-06 at 11 59 03 PM" src="https://user-images.githubusercontent.com/31358827/167242839-b546e23b-f98e-49c2-86f2-e4e0ab06e092.png">  


# Copy whole directories with scp -r  
*Description: Now you will be able to copy whole directories instead of just individual files*  

1. Show copying your whole markdown-parse directory to your ieng6 account.  
scp -r *.java *.md lib/cs15lsp22asc@ieng6.ucsd.edu:markdown-parser  
<img width="682" alt="Screen Shot 2022-05-16 at 2 43 18 PM" src="https://user-images.githubusercontent.com/31358827/168687415-fe700e90-d647-44f1-9ecb-78efa6406ccf.png">


2. Show logging into your ieng6 account after doing this and compiling
and running the tests for your repository.  
Running using my make file:  
<img width="885" alt="Screen Shot 2022-05-16 at 7 15 46 PM" src="https://user-images.githubusercontent.com/31358827/168714682-e83dfe23-6524-48c7-aea4-d73bf9c379f2.png">  
Running using normal commands:  
<img width="766" alt="Screen Shot 2022-05-16 at 6 01 05 PM" src="https://user-images.githubusercontent.com/31358827/168706339-0567a152-ced1-4f3e-bd47-fe2978786a78.png">  

3.  Show (like in the last step of the first lab) combining scp, ;, and
ssh to copy the whole directory and run the tests in one line.  
<img width="738" alt="Screen Shot 2022-05-16 at 7 29 29 PM" src="https://user-images.githubusercontent.com/31358827/168716135-1ab83834-7d35-4bee-b745-e52782ba5bf2.png">



### Steps for this section 
1. To use `scp` to copy this directory to the remote server, `cd` into the repository that you want to copy and then use this command (this will also give a name of the directory we want it to copy into on the remote server):  
`$ scp -r . cs15lsp22@ieng6.ucsd.edu:~/markdown-parse`  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(I called my repository something different to match the repository that I copied.)  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;What each command means:  
* The `-r` option tells scp to work recursively.
* The `.` is the source, and is the current directory. 
* The `~/markdown-parse` tells scp to create the markdown-parse directory on the remote server (if it doesn’t exist), and then copy the contents of this directory recursively there. If we do this, then we can log into the server with ssh and see all of our files there in a directory called markdown-parse using `scp -r . ieng6:markdown-parse`

*Note that when we do this it copies not just the files we see with ls, but all of the files in .git as well. This is fine for most uses you’ll run into. However, you can have more control over what gets copied. Try this command: `scp -r *.java *.md lib/cs15lsp22@ieng6.ucsd.edu:markdown-parse`. It will copy only the .java and .md and the lib files/folder*  

2. Then log into your remote using `scp` and `cd` into the copied repository. Compile and run your tests using `make test` if you created a Make file or `javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest`  


3. `exit` back to your local desktop. To copy the repo and run all the tests all in one line, use this command:  
`scp -r *.java *.md *.jar lib/ cs15lsp22asc@ieng6.ucsd.edu:good-markdown-parser; ssh ieng6 "cd good-markdown-parser; javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"`

If you get an error that looks like this: <img width="452" alt="Screen Shot 2022-05-16 at 7 44 32 PM" src="https://user-images.githubusercontent.com/31358827/168717667-1416a254-654c-4067-ab66-7f9638c686c9.png">
then use this command:  
`scp -r *.java *.md *.jar lib/ cs15lsp22asc@ieng6.ucsd.edu:good-markdown-parser; ssh ieng6 "cd good-markdown-parser; /software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; /software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"`  
