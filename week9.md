Title: Java file running forever    
Description: For context, here is my current working directory tree along with the contents of each file.    
![Image](assets/tree.png)    
Here, I am in the ```lab5/``` which contains ```Examples.java``` and ```test.sh```    
![Image](assets/Examples.png)    
In the ```main``` method, I create an integer array ```arr``` and a while loop that has an index ```i``` starting at zero that is meant to fill 
the array with elements equal to their indexes. My index variable ```i``` is incremented by a static method ```incrementIndex``` that takes the index
as input and increments it. After that, I print the contents of ```arr``` by using its built in ```toString``` method.       
![Image](assets/test.png)     
Here, my ```test.sh``` file compiles ```Examples.java``` and runs ```Examples.class```. This triggers the main method of ```Examples``` with additional
arguments.    
The issue here is that when I run ```bash test.sh```, no terminal output is displayed, when I expect ```{0,1,2,3,4,5,6,7,8,9}``` which is supposed to 
be the string representation of ```arr```. Instead, ```test.sh``` seems to run forever.      
![Image](assets/forever.png)       
I think there is something wrong with the way I compiled ```Examples.java```
but I am not sure. Could someone point out where things go wrong? Thank you!        


