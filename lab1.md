Brandon Panuco <br>
LAB 1

<br>
CD # 1: 
cd by itself does not change the directory path since the path is already situated at the root directory. Only way it could make a change is if I had the directory path set to a different directory other than the root directory. For example, directory path changes from lecture1/messages to the root by inputting cd with no arguments.<br>
![Image](lab1_cd1.png)

<br>
CD # 2:
cd with an argument changes the directory path to the specified folder from the last part of the path argument. In this case I specified a path change from the root directory to the lecture1 directory. If I had specified: cd lecture1/messages, then the last part of the path argument, in this case messages, would be the new path directory.<br>
![Image](lab1_cd2.png)

<br>
CD # 3:
cd with a file, in this case a txt file, as an argument produces an error. The reason why it produces an error is simply because of the purpose of the command cd, which is to change path directories and not to change the path into a file.<br>
![Image](lab1_cd3.png)

<br>
LS # 1:
ls by itself will list the files and folders in the current path. In this case ls by itself in the root directory list the only folder available, lecture1.<br>
![Image](lab1_ls1.png)

<br>
LS # 2:
ls with a directory path as an argument will list the contents found inside the provided path. In this case I wanted to know the contents of messages folder, so ls listed the files found inside messages, which were all txt files. <br>
![Image](lab1_ls2.png)

<br>
LS # 3:
ls with a file as an argument will basically provide me with the file's path. This is not an error since files can only store the file itself and not numerous files like directories are able to hold. Hence, when asking to list the directory of a file you are provided the file's path instead.<br>
![Image](lab1_ls3.png)

<br>
CAT # 1:
Providing the terminal with the cat command with no argument seems to result in an infinite loop where the terminal wait for keyboard input until a termination is requested. If I typed anything on the terminal it would have been returned back into the terminal as output. I terminated the loop by pressing ctr + c on keyboard.<br>
![Image](lab1_cat1.png)

<br>
CAT # 2:
When using a directory as an argument,in this case messages directory, on the cat command I was presented with the message letting me know that the given directory path is a directory. I feel like this is an error in which the terminal lets its user know that the user provided a non file path. This makes sense since cat is suppose to work for files only. <br>
![Image](lab1_cat2.png)

<br>
CAT # 3:
Using cat with a file path as its argument displays the contents found inside that specific file. In this case I chose to access the zh-cn.txt file, which displayed everything that was typed inside that file. <br>
![Image](lab1_cat3.png)
<br>
