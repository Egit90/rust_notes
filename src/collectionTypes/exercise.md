# Exercise

- leet code: https://leetcode.com/problems/remove-element/description/
- Given an integer array nums and an integer val, remove all occurrences of val in nums **in-place**.
- The relative order of the elements may be changed.
- You must instead have the result be placed in the first part of the array nums.
- More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result.

Example 1:

```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

---

```rust
    pub fn remove_element(nums: &mut Vec<i32>, val: i32) -> i32 {
        let mut index = 0;
        for i in 0..nums.len(){
            if nums[i] != val {
                nums[index] = nums[i];
                index += 1;
            }
        }
        println!("So we take the first {} , from the vec {:?}", index , nums);
        index as i32
    }
fn main() {
    remove_element(&mut vec![3,2,2,3],3);
}
```
