This is a simple walkthrough of Debconf, go through each and every step carefully, soon you will be using it without any trouble. Best of Luck.

--What is Debconf ?
Debconf is a backend database, with a frontend that talks to it and presents an interface to the user. There can be many different types of frontends, from plain text to a web frontend. The frontend also talks to a special config script in the control section of a debian package, and it can talk to postinst scripts and other scripts as well, all using a special protocol. These scripts tell the frontend what values they need from the database, and the frontend asks the user questions to get those values if they aren't set.

Confusing ? Let's go through the three files-config,template and script.

--Template

It contains all the notes, different questions you want to ask the user, be it boolean(true/false), multiple answer, string inputs, displaying notes, everything you want to display or ask the user.
P.S. :make sure you leave a space in the begining of the Long Description, check the file in case you have any doubt.


--Config

Next, decide what order the questions should be asked and the messages to the user should be displayed from the template file we talked about earlier.
Config script does all this, it has no other job than to display notes and questions from template file and take input from the user in the form of answers to the question it asked.

--Script

The job of this script is to use the input stored in debconf database. It all depends how you want to use the inputs, I jave just printed the inputs stored.



--Where to find the Debconf database ?

/var/cache/debconf/config.dat
config.dat stores all the template questions, notes everything you stored in the template file once you have run the config script.

--How to run the scripts ?

1. Change the permssion of the scripts to executable.
2. run the first script "sudo ./config" .You need to use sudo inorder to make changes to the debconf database.
3. run the second script "sudo ./script".

P.S. : The first script would run for only one time as after running if on the first time the flag in the debconf database gets set or "seen", but you can run the second script(script) any number of time.
If you want to run the first script(config) again, do the following:

 $ sudo gedit /var/cache/debconf/config.dat

and search the template you created and remove "seen" from all the flags of your templates, once you have deleted seen, you can run the config script again.


--That's all for the debconf, best of luck again and enjoy your experience. 



