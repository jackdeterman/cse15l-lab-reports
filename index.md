![image](Labreport1_No_Arguments.png)

For all of these commands, I am in the home directory, indicated by a "~" in the terminal. For the cd command, seemingly nothing happened when I simply ran "cd." This is because running "cd" by itself with no additional arguments changes your working directory to the home directory. Since I was already in the home directory, "cd" changed my directory to itself, and did seemingly nothing. The ls command listed all of the directories and files underneath the home directory. Since there is only one directory underneath the home directory, lecture 1, it returned "Lecture1." Finally, cat returned nothing because it expected arguments. Cat concatenates the contents of the arguments it is passed, and since I didn't give it any files or any text to concatenate, it simply returned nothing.

![image](Labreport1_directory.png)

I am once again in the home directory for all of these commands. When I used the cd command, I gave the terminal the path to the messages directory. As this is a valid directory, the terminal changed my working directory to the messages directory. When I used the ls command, I passed the home directory the path to the messages directory. As such, the terminal listed all of the files and directories in the messages directory. These included all of the txt files underneath the messages directory, including the one I added during the lab. For the cat command, I passed it the path to the messages directory as an argument. This returned an issue, because cat expects two arguments to concatenate, or combine. Since there was no text to concatenate, it returned 

![image](Labreport1_files.png)
