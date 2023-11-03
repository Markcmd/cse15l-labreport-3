# CSE15L
## Lab 3

### Part 1
+ A failure-inducing input
  ```ruby
  @Test 
  public void testReverseInPlace() {
    int[] input2 = { 4, 3, 2, 1 }; 
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{ 1,2,3,4 }, input2);
  }
  ```
+ An input that doesn’t induce a failure
  ```ruby
  @Test 
  public void testReverseInPlace() {
    int[] input1 = { 3 }; 
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
  }
  ```
+ The symptom
  ![](pic1.png)
+ The bug

  Before change
  ```ruby
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
  ```
  After Change
  ```ruby
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - 1 - i]= temp;
    }
  }
  ```
  Brief Explanation

  The original code bug happens in the for loop, which will iterate through all the array elements, but after change first half of the arr[i] with arr[arr.length - i - 1], it will change the other half of the arr[i] with arr[arr.length - i - 1], which is the same value as itselves, since we change them at previous iterations. This cause the bugs

  After fixing, I change the for loop only iterate half times as the length of the array, and in every loop I store arr[i] value in "temp" variable and change it to arr[arr.length - i - 1] and then change arr[arr.length - i - 1] value to "temp" which is previous arr[i]. This complete the reverseInPlace

### Part 2











