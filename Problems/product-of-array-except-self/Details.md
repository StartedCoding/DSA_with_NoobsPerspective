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
    prod = p * nums[i]

loop: i(0 to n)
    nums[i] = p / nums[i]

return nums
```

### But here is one obstacle in our way --> The Zero(0)

If the array has one zero(0) in it,
then:
--> product with respect to removing all the non-zero elements will be 0.
--> but, on removing the element which is equals to 0 -> we will have the product of all elements except 0.
for example:
![image.png](https://assets.leetcode.com/users/images/9b832316-0488-4269-9477-c26c52de7d76_1769944878.3920193.png)

Hmmm!
But What if we have more than one zero(0)
Then:
--> Product = 0
--> For each, removing itself, Product = 0
![image.png](https://assets.leetcode.com/users/images/efbe4bba-7c2e-4d53-a4e5-6faaf77c0a91_1769945060.0600693.png)

# Complexity

- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

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
