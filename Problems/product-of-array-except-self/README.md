# Product of Array Except Self [🔗LeetCode 238](https://leetcode.com/problems/product-of-array-except-self/description/)

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
You must write an algorithm that runs in O(n) time and without using the division operation.

Example 1:
```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```

Example 2:
```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

Constraints:
```
2 <= nums.length <= 105
-30 <= nums[i] <= 30
```
The input is generated such that answer[i] is guaranteed to fit in a 32-bit integer.

Follow up: Can you solve the problem in O(1) extra space complexity? (The output array does not count as extra space for space complexity analysis.)

---

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
So according to the problem we have to skip / remove the current index in/from the product.

Now lets see
```
if we have 2 * 3 * 4 = 24
  and we want to remove 3
    why not do 24 / 3 = 8 = 2 * 4
```
🤔 That's the intuition.

![image.png](https://assets.leetcode.com/users/images/ac21c201-965a-44e9-b691-acf3ef4b6b9c_1769942162.8539937.png)

# Approach
<!-- Describe your approach to solving the problem. -->
SO the approach would be:

## There will be two iterations for the given array:

### 1st:

In first iteration, we will find product of all elements present in the array.

### 2nd:

In the second iteration, for each element -> divide product with the element and store the value in the place of original element.

## Pseudocode:
```
prod = 1

loop: i(0 to n) 
    prod = prod * nums[i]

loop: i(0 to n)
    remaining = prod / nums[i]
    nums[i] = remaining

return nums
```

### But here is one obstacle in our way --> The Zero(0)

```
If the array has one zero(0) in it,
then:
    product with respect to removing all the non-zero elements will be 0.
    but, on removing the element which is equals to 0 -> we will have the product of all elements except 0.
```

for example:
![image.png](https://assets.leetcode.com/users/images/9b832316-0488-4269-9477-c26c52de7d76_1769944878.3920193.png)

Hmmm!
```
But, What if we have more than one zero(0)
Then:
    Product = 0 
    For each, removing itself, Product = 0
```
![image.png](https://assets.leetcode.com/users/images/efbe4bba-7c2e-4d53-a4e5-6faaf77c0a91_1769945060.0600693.png)

That means;

Case 1: 
```
If we have one zero present in the array:

    In 1st iteration: while we are calculating product
        If we find one zero:
            skip it and continue to calculate the product
                so that we could get Product that we can put in the place of the element which is equals to 0.

    In 2nd iteration: while we are modifying the array
        If we find the one zero:
            put the product there
        else for non-zero elements
            put 0 on their places
```
![image.png](https://assets.leetcode.com/users/images/9b832316-0488-4269-9477-c26c52de7d76_1769944878.3920193.png)


Case 2:
```
If we have more than one zero present in the array:
    In first iteration: while we are calculating product
    If we find one zero:
        **SAME** skip it and continue to calculate the product

    But, If we find the 2nd zero
        It means that for all element in the array (no matter if it is a zero or what), the product is going to be zero.
```
![image.png](https://assets.leetcode.com/users/images/efbe4bba-7c2e-4d53-a4e5-6faaf77c0a91_1769945060.0600693.png)

So Now;

## Pseudocode:
```
prod = 1
zeroCount = 0

loop: i(0 to n) 
    if(arr[i] == 0)
        zeroCount = zeroCount + 1

    if(arr[i] == 0 && zeroCount <= 1) // if only one zero found
        continue                      // then skip it, do nothing

    if(arr[i] == 0 && zeroCount > 1) // if more than one zero found
        prod = 0                  // then make the product = 0
        break                     // break the iteration, now for each and every element product will be 0 only

    prod = prod * nums[i]

loop: i(0 to n)
    if(arr[i] == 0)    // it will handle the DivideByZeroException
        arr[i] = prod 
        continue

    if(zeroCount > 0)
        arr[i] = 0 
        continue

    remaining = prod / nums[i]
    nums[i] = remaining

return nums
```


# Complexity
- Time complexity:
We have two seperate loops
```
O(n) 
```

- Space complexity:
We have not used any extra space
```
O(1)
```

# Code
```java []
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int p = 1;
        int rem;
        int zeroCount = 0;

        for(int i = 0; i < nums.length; i++) {
            if(nums[i] == 0) {
                zeroCount++;
            }
            
            if(nums[i] == 0 && zeroCount <= 1) {
                continue;
            }

            if(nums[i] == 0 && zeroCount > 1) {
                p = 0;
                break;
            }

            p = p * nums[i];
        }

        for(int i = 0; i < nums.length; i++) {
            if(nums[i] == 0) {
                nums[i] = p;
                continue;
            }

            if(zeroCount > 0) {
                nums[i] = 0;
                continue;
            }

            rem = p / nums[i];
            nums[i] = rem;
        }

        return nums;
    }
}
```
