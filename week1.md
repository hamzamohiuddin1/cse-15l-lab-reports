Hamza Mohiuddin Week 1 Lab Report

1. cd command: All being run in ~/lecture1
   
No arguments:   
  ```[user@sahara ~/lecture1]$ cd```   
Output:  
  ```[user@sahara ~]$```  
Explanation:  
This command put me back into the root directory ~, which is what the computer does when you run cd with no arguments. Since you are specifying an "empty" directory, it puts you in the root directory.

With a directory path as an argument:    
  ```[user@sahara ~/lecture1]$ cd ./messages```  
Output:    
  ```[user@sahara ~/lecture1/messages]$```   
Explanation:    
Since I was in the ~/lecture1 directory and the messages directory existed inside lecture1, I was able to cd into ~/lecture1/messages, a subdirectory of my previous working directory. 

With a file as an argument:   
   ```[user@sahara ~/lecture1]$ cd Hello.java```   
Output:   
   ```bash: cd: Hello.java: Not a directory```
Explanation:  
Hello.java is a java file and therefore cannot be a working directory, so I cannot cd into it. This is an error message.

2. ls command: All being run in ~/lecture1

No arguments:  
```[user@sahara ~/lecture1]$ ls```   
Output:   
```Hello.class  Hello.java  messages  README```   
Explanation:   
ls lists out the directories and files in my working directory. Because there are no arguments, the ls command just performs the ls action on my wd. Since my working directory is lecture1, the output was a list of the files and directories inside lecture1.   

With a directory as an argument:   
```[user@sahara ~/lecture1]$ ls ./messages```   
Output:   
```en-us.txt  es-mx.txt  no.txt  zh-cn.txt```   
Explanation:   
Since I specified ./messages as an argument, ls was performed on ~/lecture1/messages. Thus, the contents of the messages directory were displayed.   

With a file as an argument:   
```[user@sahara ~/lecture1]$ ls Hello.java```   
Output:   
```Hello.java```    
Explanation:   
I gave the name of the file as an input. As a result, the command line just printed the name of the file Hello.java. This is because Hello.java is not a directory and thus has no files or directories inside of it, just itself.   

3. cat command: All being run in ~/lecture1

With no argument:   
```[user@sahara ~/lecture1]$ cat```   
Output: 
```
Hello
Hello
Testing testing
Testing testing
^C
```
Explanation:   
When I pressed enter, the program waited for input from my keyboard. Every time I typed something and pressed enter, the CLI echoed what I typed until I pressed ^C to quit. Since I initially had no arguments, the CLI waited for me to type an input/argument so it could display the 'contents' of that input, which was just echoing my text.   

With a directory as an argument:   
```[user@sahara ~/lecture1]$ cat ./messages```   
Output:   

