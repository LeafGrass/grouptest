HowtoBeginGroupDeveloping
=========================


!!NOTE!!
Git Official - <http://git-scm.com/>
Github - <http://github.com/>
Actually, you can get all the help you need from <http://help.github.com/>
Text below is just a rough conclusion, which may even be incorrect.


Step 0 Install and Setup Git
----------------------------

In Fedora
	sudo yum install git gitk
Or in Ubuntu
	sudo apt-get install git gitk
Then
	git config --global user.name YOUR_NAME
	git config --global user.email 'YOUR_EMAIL'

e.g.
A new user named rescue, do it like
	git config --global user.name rescue
	git config --global user.email 'librae8226@hotmail.com'
Then you can see your info by typing in
	git config --global --list
As like:
[rescue@leafgrass workspace]$ git config --global user.name rescue
[rescue@leafgrass workspace]$ git config --global user.email 'librae8226@hotmail.com'
[rescue@leafgrass workspace]$ git config --global --list
user.name=rescue
user.email=librae8226@hotmail.com
[rescue@leafgrass workspace]$ 


Step 1 Signup at Github
-----------------------
Nothing much to say :)


Step 2 Fork A Project Repo and Work on It
-----------------------------------------
Go to LeafGrass github page, choose repo "grouoptest", then click on "Fork"
button on up right of the page. Wait a minute, this repo will be forked.

OK, for now, you've forked a project from organization LeafGrass.
Click "Dashboard" to go to your own github page and choose the repo you've
just forked.
See? There is a line represent for address of this repo, like:
    git@github.com:rescue/grouptest.git
Ok, in your local command line, run
	git clone git@github.com:rescue/grouptest.git

Then, I guess you'll meet a problem below, like:
[rescue@leafgrass workspace]$ git clone git@github.com:rescue/grouptest.git
Cloning into grouptest...
The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,207.97.227.239' (RSA) to the list of
known hosts.
Permission denied (publickey).
fatal: The remote end hung up unexpectedly

This is because you don't have SSH keys. Everyone need a private key and a
public key for himself, and may get many other's public keys, so people can work
and communicate together.
Follow these steps in link below, you can resolve it.
<http://help.github.com/linux-set-up-git/>

e.g.
[rescue@leafgrass workspace]$ cd ~/.ssh/
[rescue@leafgrass .ssh]$ ls
known_hosts
[rescue@leafgrass .ssh]$ ssh-keygen -t rsa -C librae8226@hotmail.com
Generating public/private rsa key pair.
Enter file in which to save the key (/home/rescue/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/rescue/.ssh/id_rsa.
Your public key has been saved in /home/rescue/.ssh/id_rsa.pub.
The key fingerprint is:
d6:2d:09:1f:32:c6:c7:d2:b7:c5:74:a3:ef:9d:f1:ea librae8226@hotmail.com
The key's randomart image is:
+--[ RSA 2048]----+
|              ...|
|       . o   o...|
|        B = ..o  |
|       . O = o.  |
|        S = o  o |
|       .   .  . =|
|               oo|
|               . |
|             .E  |
+-----------------+
[rescue@leafgrass .ssh]$ cat id_rsa.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDOXdY5RscN1gumTa0ZqNfTJ631WsK6Nwlaj9Bofk38kqLa6hI5RQ5SrmGG1EIH22is1wa1xCpSg2I6villDCUwfZcDc5ecyThLmaq44jip7Vle85LU3oSpJ/3Ak2ve/hP/ZrF4lZsd9fdvWwsj8jce2ZAspgrQELvAzfc7MqUWcBKyRuSQgwaWJLd1SozIn7Bm7BoHkTsaVo7qoKxrV+BSHY7/N/pPYXBkfZjXett0p2rBst7gBIKOB/vKesI9tK/lG8iAKnGTOAWJuCyxYwAWKjeJ2W1enGzf6m1tmzj3jJfvl2hLAlcyqYS1e6MUGyD0Hbn3aH0t9mcRwRThc6wx librae8226@hotmail.com
[rescue@leafgrass .ssh]$

On the GitHub site Click “Account Settings” > Click “SSH Public Keys” > Click
“Add another public key”.
Copy the WHOLE output string like above to the "Key" field.
("Title" is not neccessary.)
Then click on "Add key", everything is ok. The "clone" action can be done now.

e.g.
[rescue@leafgrass workspace]$ git clone git@github.com:rescue/grouptest.git
Cloning into grouptest...
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 6 (delta 1), reused 6 (delta 1)
Receiving objects: 100% (6/6), 25.11 KiB, done.
Resolving deltas: 100% (1/1), done.
[rescue@leafgrass workspace]$ ls
grouptest

OK? Go forward next step.


Step 3 Basic Working on Local
-----------------------------
	cd grouptest
	git pull
	[do some changes]
	git add .
	git status
	git commit -a
	[type in your commit comment]
	git push

e.g.
[rescue@leafgrass grouptest]$ git pull
Already up-to-date.
[rescue@leafgrass grouptest]$ ls
license.md  markdown.pl  readme.md  syntax.md
[rescue@leafgrass grouptest]$ echo testing > test.md
[rescue@leafgrass grouptest]$ ls
license.md  markdown.pl  readme.md  syntax.md  test.md
[rescue@leafgrass grouptest]$ git add .
[rescue@leafgrass grouptest]$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#	new file:   test.md
#
[rescue@leafgrass grouptest]$ git commit -a
[master 0cc4938] test
 1 files changed, 12 insertions(+), 0 deletions(-)
 create mode 100644 test.md
[rescue@leafgrass grouptest]$ git push
Counting objects: 4, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 300 bytes, done.
Total 3 (delta 1), reused 0 (delta 0)
To git@github.com:rescue/grouptest.git
   d0bc323..0cc4938  master -> master
[rescue@leafgrass grouptest]$

Well, now turn to you github page and you'll see all your changes.

Actually, that's all for regular code updating, modifying and uploading.
Please see git documents for detailed information of these commands and other
advanced usage.


Step 4 Pull Request
-------------------
Two terms here: push and pull.
push: After you commit your changes in you local repo, "push" will upload your
changes to the server(that is, our repository) and do an auto-merge.
pull: Download the latest files from server to your local repo(in fact, current
branch) then do an auto-merge, too.

On the page of your github repo, click on the "Pull Request" up right.
Then it will prompt a new page require you to fill in the requesting message,
just like writing an E-Mail.
Actually in this step, you are requesting the administrator of the repo you
just forked to merge your changes into the main repo in Organization LeafGrass.
Then you can see a line like this on github page:
rescue wants someone to merge 1 commit into LeafGrass:master from rescue:master

Thus, the repo administrator will receive an E-Mail like this:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
rescue reply+i-1703947-fbed3312508d7ba9a649fc58...@reply.github.com to me
	
This is just for pull request test.

You can merge this Pull Request by running:

 git pull https://github.com/rescue/grouptest master

Or you can view, comment on it, or merge it online at:

 https://github.com/LeafGrass/grouptest/pull/1

-- Commit Summary --

* test

-- File Changes --

A test.md (12)

-- Patch Links --

 https://github.com/LeafGrass/grouptest/pull/1.patch
 https://github.com/LeafGrass/grouptest/pull/1.diff

--
Reply to this email directly or view it on GitHub:
https://github.com/LeafGrass/grouptest/pull/1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Why pull request instead of direct push?
Look at this page - <http://help.github.com/send-pull-requests/>


Step 4 Development in the Future
--------------------------------
After we get to be familiar with this fast version control system - Git, each of
us developers need a direct acess to the base repo for a faster developing
process.
Thus, one can create his own branch based on the latest master(trunk), and works
on it. Developing new features or fixing bugs will be done on this branch.
Ofcourse, he SHOULD take charge of his branch's healthy.
As this specific feature is implemented or bug is fixed, and passed the testing,
We can merge it to our trunk - master.


Let's do to help the source tree growing up ...
Thanks.

