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
