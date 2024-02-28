Part 1 - Bugs    
Buggy program: reverseInPlace(array)   
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```    
1. Failure inducing input:
```
     public void testReverseInPlace() {
       int[] input1 = { 1, 2, 3, 4, 5 };
       ArrayExamples.reverseInPlace(input1);
       assertArrayEquals(new int[]{ 5, 4, 3, 2, 1 }, input1);
     }
```
2. Non-failure input:
```
public void testReverseInPlace2() {
     int[] input1 = { 1, 2, 3, 2, 1};
     ArrayExamples.reverseInPlace(input1);
     assertArrayEquals(new int[]{ 1, 2, 3, 2, 1 }, input1);
   }
```
3. The symptom:
![Error](./assets/error)
4. Before and After:      
   -Before:    
   ```
   static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
   }
   ```
   -After:
   ```
   static void reverseInPlace(int[] arr) {
    int[] copy = new int[arr.length];
    for(int i=0;i<arr.length;i++){
      copy[i] = arr[i];
    }
    for(int i = 0; i < arr.length; i++) {
      arr[i] = copy[arr.length - i - 1];
    }
   }
   ```
Part 2: Researching commands - find    
1. -name pattern:
   ```
   [user@sahara ~/docsearch/technical]$ find -name 'chapter*'
	./911report/chapter-5.txt
	./911report/chapter-13.1.txt
	./911report/chapter-12.txt
	./911report/chapter-11.txt
	./911report/chapter-1.txt
	./911report/chapter-10.txt
	./911report/chapter-13.4.txt
	./911report/chapter-8.txt
	./911report/chapter-6.txt
	./911report/chapter-7.txt
	./911report/chapter-3.txt
	./911report/chapter-13.5.txt
	./911report/chapter-2.txt
	./911report/chapter-13.3.txt
	./911report/chapter-13.2.txt
	./911report/chapter-9.txt
	[user@sahara ~/docsearch/technical]$ find -name '*6750*.txt'
	./biomed/1472-6750-3-4.txt
	./biomed/1472-6750-2-14.txt
	./biomed/1472-6750-1-11.txt
	./biomed/1472-6750-3-11.txt
	./biomed/1472-6750-3-6.txt
	./biomed/1472-6750-1-13.txt
	./biomed/1472-6750-2-13.txt
	./biomed/1472-6750-1-8.txt
	./biomed/1472-6750-1-12.txt
	./biomed/1472-6750-1-6.txt
	./biomed/1472-6750-2-21.txt
	./biomed/1472-6750-2-2.txt
	./biomed/1472-6750-2-10.txt
   ```      
   -name lets you specify a name or pattern you want to look for in the specified directory. In this case there are a lot of files so looking with a specific number/code helps me narrow them down. This is useful if you are in someone else's server and want to look for a file that you did not create. From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/.     
2. -type type:
   ```
   [user@sahara ~/docsearch/technical]$ find -type d
	.
	./911report
	./biomed
	[user@sahara ~/docsearch/technical]$ find -name '*6750*.txt' -type f
	./biomed/1472-6750-3-4.txt
	./biomed/1472-6750-2-14.txt
	./biomed/1472-6750-1-11.txt
	./biomed/1472-6750-3-11.txt
	./biomed/1472-6750-3-6.txt
	./biomed/1472-6750-1-13.txt
	./biomed/1472-6750-2-13.txt
	./biomed/1472-6750-1-8.txt
	./biomed/1472-6750-1-12.txt
	./biomed/1472-6750-1-6.txt
	./biomed/1472-6750-2-21.txt
	./biomed/1472-6750-2-2.txt
	./biomed/1472-6750-2-10.txt
    ```
-type lets you specify the type of file you want to find, whether it is d (directory), or f (file). In this case I am looking for files and not directories. This is useful if there are files that have the same name as their directory. From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/    
  3. -size [+/-]n:    
  ```
[user@sahara ~/docsearch/technical]$ find . -size +500
	./911report/chapter-13.4.txt
	./911report/chapter-3.txt
	./911report/chapter-13.5.txt
	[user@sahara ~/docsearch/technical]$ find . -size +500 -size -550
	./911report/chapter-13.4.txt
	./911report/chapter-3.txt
  ```
-size lets you specify a number of characters that you want your files to be above or below. +n means above n characters, -n means below n characters. In this case, 1 of the files is above 500 but also above 550, so it doesn't fall within the 500-550 window. This is useful if you have multiple files of the same name that are of varying sizes, but you don't want to look directly. From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/     
4. -empty    
```
[user@sahara ~/docsearch/technical]$ find ./911report/ -empty
[user@sahara ~/docsearch/technical]$ find ./biomed/ -empty -name '*61*'
./biomed/ar615.txt
./biomed/ar612.txt
./biomed/ar619.txt
./biomed/bcr618.txt
```
-empty lets you specify that you are looking for files that are empty. This is useful if you want to delete empty files, but don't know which files are empty. In this case, several files are empty so they may not be useful. From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/     

