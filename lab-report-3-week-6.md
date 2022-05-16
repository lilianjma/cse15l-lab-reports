# Streamline ssh Configuration  
1. Show your .ssh/config file, and how you edited it (with VScode, another program, etc)  
<img width="752" alt="Screen Shot 2022-05-05 at 9 35 03 PM" src="https://user-images.githubusercontent.com/31358827/167067700-456b06de-054d-4553-b646-3e9b67abb1c7.png">

2. Show the ssh command logging you into your account using just the alias you chose.  
<img width="717" alt="Screen Shot 2022-05-05 at 9 36 08 PM" src="https://user-images.githubusercontent.com/31358827/167067778-93f4d630-0849-40fe-8d54-99fe8b7378b2.png">

3. Show an scp command copying a file to your account using just the alias you chose.  
<img width="689" alt="Screen Shot 2022-05-06 at 8 04 04 PM" src="https://user-images.githubusercontent.com/31358827/167235550-b8dcfde3-10cd-4024-a4ea-9125ee4e72e8.png">


### Steps for this section  
1. Open or create ~/.ssh/config on your computer
2. Add these lines: 
``Host ieng6
HostName ieng6.ucsd.edu
User cs15lsp22zzz (use your username)``
3. And then try this command: `ssh ieng6`
4. If things are set up correctly, this should use the key and log you in with the username you specified using your public key. If this doesn’t work, you can try adding a line to explicitly refer to yourid_rsa file:
``Host ieng6
HostName ieng6.ucsd.edu
User cs15lsp22zzz (use your username)
IdentityFile ~/.ssh/id_rsa``
5. Then you should be able to use ieng6 in place of your account name.



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
1. Show copying your whole markdown-parse directory to your ieng6 account.  
scp -r *.java *.md lib/cs15lsp22asc@ieng6.ucsd.edu:markdown-parser
<img width="1088" alt="Screen Shot 2022-05-07 at 1 50 02 PM" src="https://user-images.githubusercontent.com/31358827/167271281-4b6f9dfa-b184-41b2-a562-eafa42ce015c.png">  

2. Show logging into your ieng6 account after doing this and compiling
and running the tests for your repository.  
<img width="1088" alt="Screen Shot 2022-05-07 at 1 50 49 PM" src="https://user-images.githubusercontent.com/31358827/167271307-aa9c1d27-1bff-42b9-9444-5c86bfa4dd58.png">

3.  Show (like in the last step ofthe firstlab) combining scp, ;, and
ssh to copy the whole directory and run the tests in one line.  
<img width="1088" alt="Screen Shot 2022-05-07 at 1 50 49 PM" src="https://user-images.githubusercontent.com/31358827/167271307-aa9c1d27-1bff-42b9-9444-5c86bfa4dd58.png">  
*Note: I scp two different MarkdownParsers, the one that I copy in the screenshots had an unresolved infinite loop, that is why it prints "This method ran" like a bajillion times, so I could not scroll up to find the actual command that I used, that is why I used a different MarkdownParser directory that I had coppied before to run the command.*


### Steps for this section 
1. Usescp to copy this directory to the remote server. 
2. We also have to give a name of the directory we want it to copy into on the remote server:
`$ scp -r . cs15lsp22@ieng6.ucsd.edu:~/markdown-parse`
3. The-r option tellsscp to work recursively. The. is thesource, and is the currentdirectory. The~/markdown-parse tells scp to create the markdown-parse directory on the remote server (if it doesn’t exist), and then copy the contents of this directory recursively there.
If we do this, then we can log into the server withssh and see all of our files there in a
directory calledmarkdown-parse using `scp -r . ieng6:markdown-parse`
4. Note that when we do this it copies not just the files we see with ls, but all of the files in .git as well. This is fine for most uses you’ll runinto. However, you can have more control over what gets copied. Try this command: `scp -r *.java *.md lib/cs15lsp22@ieng6.ucsd.edu:markdown-parse`
