Python版本：

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        tmp = {}
        for index, value in enumerate(nums):
            if (target-value) in tmp:
                return [index, tmp[target-value]]
            else:
                tmp[value] = index
        return 
        
```

Java版本：

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        int[] result = {-1, -1};
        for (int i=0; i<nums.length; i++)
        {
            if (map.containsKey(target-nums[i]))
            {
                result[0] = map.get(target-nums[i]);
                result[1] = i;
                return result;
            }else
            {
                map.put(nums[i], i);
            }
        }
        return result;
    }
}
```