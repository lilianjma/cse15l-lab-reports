# Installing VS Code

Go to this url for (downloading VS Code)[https://code.visualstudio.com/download] and then choose the download button corresponding to the computer that you have. The page should look like this:

<img width="1440" alt="Screen Shot 2022-04-18 at 5 18 24 PM" src="https://user-images.githubusercontent.com/31358827/163896484-97aee2a5-6aa6-469a-8f94-6a2144013cb8.png">

After it downloads, you should open the file and follow the instructions that it tells you.

# Remotely Connecting

To remotely connect, you must use the command, `ssh cs15lsp22zz@ieng6.ucsd.edu` in your terminal where the `zz` is replaced with your course specific account. Mine is `asc` as shown below.

<img width="1552" alt="Screen Shot 2022-04-18 at 5 25 40 PM" src="https://user-images.githubusercontent.com/31358827/163897063-b5c40dc1-ad3b-44d6-a310-1eda2b3544f6.png">

When you first connect, you must say yes to questions and enter your password.

# Important Terminal Commands

 Note: depending on your computer, the start of a new comman will be "$" or for me it is "\%". I will just be using "\$" to depict when a new command starts.

### Command 1: $ls

Typing in `$ls` will create a list of the all the files in the directory besides the hidden files that start with "." as shown below.

<img width="682" alt="Screen Shot 2022-04-07 at 3 41 46 PM" src="https://user-images.githubusercontent.com/31358827/162331435-90a9ed20-bd28-4f02-b16c-5407fec55488.png">

### Command 2: $ls -a

Typing in `$ls -a` will create a list of the all the files in the directory including the files that start with "." as shown below.

<img width="682" alt="Screen Shot 2022-04-07 at 3 42 01 PM" src="https://user-images.githubusercontent.com/31358827/162331456-d74ccca8-4b47-4008-a0e8-a1bb3a3db14c.png">

### Command 3: $cd

Typing in `$cd ` and then the name of a directory will move you to that directory. In the screenshot below, I have a folder called "UCSD" so when I use the command `$cd UCSD`, I am moved into that directory and can then access the other directories and files in UCSD. As you can see, next to the cruiser in the terminal, it says "lilian@Lilians-MackBook-Pro UCSD %" instead of what it had before, which was "lilian@Lilians-MackBook-Pro ~ %" showing that I moved from the root directory, denoted by the "~" into a directory in it called "UCSD".

<img width="682" alt="Screen Shot 2022-04-07 at 3 42 23 PM" src="https://user-images.githubusercontent.com/31358827/162331468-2aeb7c73-a430-4801-9d09-c25f683c0b1c.png">

### Command 4: $cd ..

Typing in `$cd ..` move you from your current directory into its parent directory. As seen below, I was in the "UCSD" directory and then after using the command I moved into its parent directory which also happened to be the root directory.

<img width="682" alt="Screen Shot 2022-04-07 at 3 42 38 PM" src="https://user-images.githubusercontent.com/31358827/162331478-66b27e0c-ce07-4f59-a840-ee33e3d32f24.png">

### Command 5: $pwd

`$pwd` is another way to see which directory you are in aka it shows the file path to the directory that you are in.

<img width="682" alt="Screen Shot 2022-04-10 at 6 47 09 PM" src="https://user-images.githubusercontent.com/31358827/162651638-17be788f-c8d4-43d7-a8c7-dfdc3688e212.png">



### Command 4: $clear

If you want to clear the screen of your terminal, use `$clear`. It will not delete your past commands so you can still use the up and down arrow keys to access your past commands.

Before pressing enter:

<img width="682" alt="Screen Shot 2022-04-10 at 6 47 39 PM" src="https://user-images.githubusercontent.com/31358827/162651672-1aabc8f2-9ddf-4230-ac4a-a6f70a5a4212.png">

After pressing enter:

<img width="682" alt="Screen Shot 2022-04-10 at 6 48 12 PM" src="https://user-images.githubusercontent.com/31358827/162651713-1dbea16a-be32-4dab-a739-15f5370936f3.png">


# Moving Files with `scp`

To move a file from your computer to the remote computer, you use the command, `scp [filename] cs15lsp22zz@ieng6.ucsd.edu:~/` where `[filename]` is the name of the file that you want to move and `zz` is the name of your course specific account. You must make sure that you are on your computer in the terminal, as you can see my terminal says `lilian@Lilians-MacBook-Pro` denoting that I am on my computer rather than connected to the remote computer. The file that I moved was called WhereAmI.java and after you run the command it should look like this:

<img width="1552" alt="Screen Shot 2022-04-18 at 5 39 33 PM" src="https://user-images.githubusercontent.com/31358827/163898069-1282accb-c3e1-45db-a786-9f730ef3317c.png">

# Setting an SSH Key

To set an ssh key so you do not have to use a password, first use this command in your terminal on your client `ssh-keygen`, then use the following series of commands for the following questions:

* Enter file in which to save the key (/Users/lilian/.ssh/id_rsa): `/Users/<your username here>/.ssh/id_rs`
* Enter passphrase (empty for no passphrase):
* Enter same passphrase again:

You do not want to enter anything in for the paraphrase, just press enter both times. Then log into you remote server and use the command `mkdir .ssh`. Your terminal should look mostly like this:

<img width="691" alt="Screen Shot 2022-04-18 at 5 53 42 PM" src="https://user-images.githubusercontent.com/31358827/163899137-e1fc5b70-b2e7-4744-ad60-eee5ee8d14bf.png">

Then log out of your remote server and use the following command: `scp /Users/<your username here>/.ssh/id_rsa.pub cs15lsp22zz@ieng6.ucsd.edu:~/.ssh/authorized_keys` and enter your password. Now, when you use scp you will not need to enter your password.

It will look something like this and now you will be able to save time:

<img width="937" alt="Screen Shot 2022-04-18 at 6 04 16 PM" src="https://user-images.githubusercontent.com/31358827/163899917-d8e0aec2-3a22-4bff-bc41-2e53c9afd366.png">

# Optimizing Remote Running

In the screenshot directly above, you can see that I used the command `ssh cs15lsp22asc@ieng6.ucsd.edu "ls"` to log into the remote server then get a list of the files all in one command. Below that command you can see I use semicolons to separate different commands so I can run them all at once. An example of optimizing remote running is by combining these two ideas and here you can see I connect to the remote server then I copy a WhereAmI.java into a new file called OtherMain.java and then I compile and run OtherMain.java and I use ls to list all of the files: 

<img width="916" alt="Screen Shot 2022-04-18 at 6 11 02 PM" src="https://user-images.githubusercontent.com/31358827/163900467-421ed156-415e-4652-9673-c2b5670a70df.png">
