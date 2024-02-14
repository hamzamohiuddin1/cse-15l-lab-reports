Part 1 - Bugs    
Buggy program: reverseInPlace(array)   
1. Failure inducing input:
2. ```
     public void testReverseInPlace() {
       int[] input1 = { 1, 2, 3, 4, 5 };
       ArrayExamples.reverseInPlace(input1);
       assertArrayEquals(new int[]{ 5, 4, 3, 2, 1 }, input1);
     }
  ```
3. 
