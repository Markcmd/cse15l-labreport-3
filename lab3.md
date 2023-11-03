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
```ruby


```
