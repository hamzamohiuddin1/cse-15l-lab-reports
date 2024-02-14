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

2. Non-failure input:
   ```
        public void testReverseInPlace2() {
             int[] input1 = { 1, 2, 3, 2, 1};
             ArrayExamples.reverseInPlace(input1);
             assertArrayEquals(new int[]{ 1, 2, 3, 2, 1 }, input1);
	   }
3. The symptom:
   ```
   (base) hamza@Hamzas-Laptop lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
     JUnit version 4.13.2
     ..E.
     Time: 0.004
     There was 1 failure:
     1) testReverseInPlace(ArrayTests)
     arrays first differed at element [3]; expected:<2> but was:<4>
             at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
             at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
             at org.junit.Assert.internalArrayEquals(Assert.java:534)
             at org.junit.Assert.assertArrayEquals(Assert.java:418)
             at org.junit.Assert.assertArrayEquals(Assert.java:429)
             at ArrayTests.testReverseInPlace(ArrayTests.java:9)
             ... 32 trimmed
     Caused by: java.lang.AssertionError: expected:<2> but was:<4>
             at org.junit.Assert.fail(Assert.java:89)
             at org.junit.Assert.failNotEquals(Assert.java:835)
             at org.junit.Assert.assertEquals(Assert.java:120)
             at org.junit.Assert.assertEquals(Assert.java:146)
             at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
             at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
             ... 38 more
     
     FAILURES!!!
     Tests run: 3,  Failures: 1
     ```
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
   -name lets you specify a name or pattern you want to look for in the specified directory. From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/.
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
-type lets you specify the type of file you want to find, whether it is d (directory), or f (file). From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/    
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
-size lets you specify a number of characters that you want your files to be above or below. +n means above n characters, -n means below n characters. From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/     
4. -empty    
```
[user@sahara ~/docsearch/technical]$ find ./911report/ -empty
[user@sahara ~/docsearch/technical]$ find ./biomed/ -empty -name '*61*'
./biomed/ar615.txt
./biomed/ar612.txt
./biomed/ar619.txt
./biomed/bcr618.txt
```
-empty lets you specify that you are looking for files that are empty. From https://www.geeksforgeeks.org/find-command-in-linux-with-examples/     

