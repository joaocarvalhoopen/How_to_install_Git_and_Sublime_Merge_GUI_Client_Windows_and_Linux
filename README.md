# How to install Git and Sublime Merge GUI Client Windows and Linux
A guide for Windows and Linux.

# How to configure Git and Git Sublime Merge in Windows.


## Install Git

* Git Download link <br>
  [https://git-scm.com/download/win](https://git-scm.com/download/win) <br>


**Install with the following options** <br>

```
1º Screen
Select components

V – Windows Explorer Integration
        V - Git Bash Here
        V – Git GUI Here
V - Git LFS (Large File Support)
V - Associate .git* configuration files with the default text editor
V – Associate .sh files to be run with Bash

2º Screen
Adjusting your PATH environment

V – Git from the command line and also from 3rd-party software.

3º Screen
Choosing the SSH executable

V – Use OpenSSH

4º Screen
Choosing HTTPS transport backend

V – Use the OpenSSL library

5º Screen
Configuring the line ending conversions

V - Checkout as-is, commit as-is

6º Screen 
Configure the terminal emulator to use Git Bash

V – Use Windows default console window
```


## Configuring Git on your computer, user, email address and editor - Windows
 
1. Install an editor, to edit your git diffs in case of the code conflicts and merges, I use Visual Studio Code, Sublime Merge uses by default Sublime Text. <br>
     [https://code.visualstudio.com/](https://code.visualstudio.com/) <br>
  
 
2. On you computer (Windows), open the Git Bash and do the following. Determine in your remote repository, if your user starts with a @ symbol before, if it has don’t forget the first symbol in the start of the username: <br>
```
git config --global user.name "maria.jaquina"
or 
git config --global user.name "@maria.jaquina"

git config --global user.email "maria.jaquina1900@gmail.com"
git config --global core.editor "code -w"

To see if all is correct do:
git config --global user.name
git config --global user.email
git config --global core.editor
```


## Then you have to generate the SSH private and public keys: <br>

1. Still In the Git Bash, not CMD - Command Line, do <br>
   ```cd .ssh``` <br>
   Don’t forget the “.” (dot) it’s a hidden directory then, and only inside this directory do the following, with your email: <br>
   ```ssh-keygen -t rsa -b 2048 -C "maria.jaquina1900@gmail.com"``` <br>
   In the file name, fill in with the name: <br>
   "id_rsa" with out the quotes ```:-)``` <br>
   And fill in the passphrase for the private key that you can’t forget, because it will be asked to you when you interact with Sublime Merge more precisely pageant by SSH for example to make a Clone, or Commit followed by a Push. <br>
   The directory where the files where generated was on Windows 11 <br>
   ```C:/Users/mariajaquina/.ssh/```
   There are two files that will be created there, one that is .pub, the public key and the other a private key. <br>
   There is also a previous hosts file, that we will not use. <br> 

4. With the public key id_rsa.pub file, open in notepad and copy all the text, and be very careful to not add or remove any character and that includes spaces. Do a Ctrl + C .

5. Open your Github or Gitlab or the private repository of your enterprise, and in the upper right corner click on the user and choose edit profile. There you will see on the left side list panel a link to the SSH Keys. Click in it.

6. Now with the content that you had on CTRL-C, with the public key text, add it in the open space, the title of the key will be filled automatically, by your comment that you filled while generating the pair of keys, and should be your email. Then add a  public key expiration date, for example one moth or one year in the future (should be a small period, for security reasons) and click the button add or save.


## How to install Putty to manage the keys for Sublime Merge in Windows.

See the last section in the following Getting Started Guide: <br>

```WINDOWS: SETTING UP PUTTY / PLINK / PAGEANT WITH SUBLIME MERGE``` <br>
[https://www.sublimemerge.com/docs/getting_started#authentication](https://www.sublimemerge.com/docs/getting_started#authentication) <br>


### Know you will be importing the SSH keys into Putty.

1. Get Putty from here <br>
   [https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

2. Run PuttyGen and select ```Conversions -> Import Key``` .

3. Select id_rsa key ```~/.ssh/id_rsa``` not the ".pub" like is in the Getting Started manual.

4. Save a copy of the private key to the same folder and of the public key.


### Now that the key is saved, we will be enabling plink/PuTTy in sublime Merge.

1. In  Sublime Merge and select ```Preferences -> Preferences…```

2. In the preferences dialog choose Advanced.

3. Navigate to SSH Path, and set this to the plink system path ```(likely C:\Program Files\PuTTY\plink.exe)```.


### Sublime Merge is using plink, the last step is to start pageant (comes with PuTTy) and load in your credentials. This ensures you don't have to enter your SSH credentials every time you perform a remote operation.

1. Start the pageant executable.

2. Once started, you'll find the pageant icon in the system tray. Right click the icon and select Add Key.

3. Navigate to and select the private key you saved earlier.


### To start pageant at startup, do

1. See the following: <br>
   ```chunter/pageant-autoload-keys-at-startup.txt``` <br>
   [https://gist.github.com/chunter/3ec25dd802c2163265eacfcb6f53cb7d](https://gist.github.com/chunter/3ec25dd802c2163265eacfcb6f53cb7d) <br>



# How to configure Git and Git Sublime Merge in Linux.


## Install Git - Linux

1. Fedora 36 already comes with Git Installed but on Ubuntu you have to install it.

2. Git Download link <br>
   [https://git-scm.com/download/](https://git-scm.com/download/) <br>


## Configuring Git on your computer, user, email address and editor – Linux

1. Install an editor, to edit your git diffs in case of the code conflicts and merges, I use Visual Studio Code, Sublime Merge uses by default Sublime Text. <br>
   [https://code.visualstudio.com/](https://code.visualstudio.com/) <br>
  
 
2. On you computer (Linux), open a terminal, the Bash for example and do the following. Determine in your remote repository if your user starts with a @ symbol before, if it has don’t forget the first  symbol in the start of the username: <br>
```
git config --global user.name "maria.jaquina"
or 
git config --global user.name "@maria.jaquina"

git config --global user.email "maria.jaquina1900@gmail.com"
git config --global core.editor "code -w"

To see if all is correct do:
git config --global user.name
git config --global user.email
git config --global core.editor
```


## Then you have to generate the SSH private and public keys on Linux <br>

1. Still In the terminal in fedora 36, ubuntu should be very similar, do <br>
   ```mkdir ~/.ssh``` <br>
   ```cd .ssh``` <br>
   Don’t forget the “.” (dot) it’s a hidden directory then, and only inside this directory do the following, with your email: <br>
   ```ssh-keygen -t rsa -b 2048 -C "maria.jaquina1900@gmail.com"``` <br>
   In the file name, fill in with the name: <br>
   "id_rsa" with out the quotes ```:-)``` <br>
   And fill in the passphrase for the private key that you can’t forget, because it will be asked to you when you interact with Sublime Merge more precisely pageant by SSH for example to make a Clone, or Commit followed by a Push. <br>
   The directory where the files where generated on Linux: <br>
   ```/home/mariajaquina/.ssh/```
   There are two files that will be created there, one that is .pub, the public key and the other without the extension is the private key. <br>
   Then we will add the private key to the ssh-agent: <br>
   ```ssh-add  ~/.ssh/id_rsa``` <br>
   You have to REBOOT the machine, so that changes take effect. <br>
   All is made, but you can also see the Sublime Merge Getting Started Manual in here: <br>
   ```AUTHENTICATING VIA SSH``` <br>
   [https://www.sublimemerge.com/docs/getting_started#authentication](https://www.sublimemerge.com/docs/getting_started#authentication) <br>

4. With the public key id_rsa.pub file, open in a editor ex: Sublime Text and copy all the text, and be very careful to not add or remove any character and that includes spaces. Do a Ctrl + C .

5. Open your Github or Gitlab or the private repository of your enterprise, and in the upper right corner click on the user and choose edit profile. There you will see on the left side list panel a link to the SSH Keys. Click in it.

6. Now with the content that you had on CTRL-C, with the public key text, add it in the open space, the title of the key will be filled automatically, by your comment that you filled while generating the pair of keys, and should be your email. Then add a public key expiration date, for example one moth or one year in the future (should be a small period, for security reasons) and click the button add or save.


## How to use it in sublime Merge in Linux.

1. Sublime Merge just uses the settings from Git command line, so you don't have to make any other configurations.


## How to use two different Git Users to access two different Git Repository servers.

1. First, you only use one SSH key for both the servers, so you register the same key on both, there is the possibility to have different key but you have to generate two keys and be changing the used key every time you use it with the ssh-add command. So the best way is to use one SSH Key for all Git Servers.

2. In Sublime Merge you don't have the concept of starting the program with a specific user, it starts a clone or a new git project with you global user.name  and global user.email settings and then it attributes it to the project internal setting and one uses what's configured in the project afterwards.

3. But when you need multiple users, you clone with your main global user (the local clone user and email isn't checked by the Git Server, only the SSH and the password is), and then after the clone or the creation of a new Git Project, you can change for the specific user by clicking on the right side panel on it, and choosing you specific user and specific email for the project.

4. See the following post response on the Sublime Merge Forum: <br>
   Linux - Two different users in two different repos in Sublime Merge <br>
   [https://forum.sublimetext.com/t/linux-two-different-users-in-two-different-repos-in-sublime-merge/65410/2](https://forum.sublimetext.com/t/linux-two-different-users-in-two-different-repos-in-sublime-merge/65410/2) <br>        


## Have fun
Best regards, <br>
João Nuno Carvalho



