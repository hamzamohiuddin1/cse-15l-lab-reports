Step 4: Log into ieng6    
![Step 4](./assets/lab7/step1.png)    
First, I typed into my terminal ```ssh hmohiuddin@ieng6.ucsd.edu<enter>```. Since I had my ssh keys registered, I did not have to enter any password and I successfully ssh'ed into the server.    
Step 5: Clone your fork of the repository from your Github account (using the SSH URL)     
Step 6: Run the tests, demonstrating that they fail      
![Step 5](./assets/lab7/step2.png)     
First, I typed  ```git clone <^v> <enter>``` since I had the ssh url for my forked repo copied onto my keyboard. This cloned the repository. Then I typed ```cd l<tab><enter>```. Since ```/lab7``` was the only directory/file in the working directory that started with 'l', I only had to type ```l``` and press ```<tab>``` and it auto-filled to ```cd lab7```. Then I typed ```bash t<tab><enter>```. ```test.sh``` was the only file in ```lab7``` that started with ```t```, so pressing ```<tab>``` auto-filled to ```bash test.sh```. This ran the tests and displayed the results. Then I typed ```vim L<tab>.j<tab><enter>```. Since ```ListExamples.java``` is the only file that starts with ```L```, it was autofilled to ```vim ListExamples```. Then I typed ```.j``` to specify that I am looking for ```ListExamples.java``` and not ```ListExamplesTests.java```. This autofilled to ```vim ListExamples.java```. This put me into the vim editor.      
Step 7: Edit the code to fix the failing test    
![Step 7](./assets/lab7/step3.png)

