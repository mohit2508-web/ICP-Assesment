# 121. Best Time to Buy and Sell Stock
## Question_Link : https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/
## Solution_Link : https://leetcode.com/problems/best-time-to-buy-and-sell-stock/submissions/1883642840

## Code 
```
class Solution {
    public int maxProfit(int[] prices) {
        int buy =0 ;
        int profit=0;
        for(int i=0;i<prices.length;i++){
            buy=prices[i];
            for(int j=i+1;j<prices.length;j++){
                if(prices[j]>buy){
                    profit= Math.max(profit,prices[j]-buy);
                    
                }
            }
        }
        return profit;
    }
}

```

# 28. Find the Index of the First Occurrence in a String
## Solution_Link : https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/submissions/1892971919

## Code
```
class Solution {
    public int strStr(String haystack, String needle) {
        int haylen= haystack.length();
        int needlelen =needle.length();
        if (haylen < needlelen) {
            return -1;
        }
        for (int i =0; i <=haylen -needlelen;i++) {
            int j = 0;
            while (j < needlelen &&haystack.charAt(i + j) == needle.charAt(j)) {
                j++;
            }
            if (j ==needlelen) {
                return i;
            }
        }
        return -1;
    }
}
```

# 15. 3Sum
## Solution_Link : https://leetcode.com/problems/3sum/submissions/1892980028

## Code 
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res= new ArrayList<>();
        Arrays.sort(nums);
        for (int i = 0; i<nums.length; i++) {
            if (i>0 && nums[i] == nums[i-1]) {
                continue;
            }  
            int j = i + 1;
            int k = nums.length-1;
            while (j < k) {
                int total = nums[i] + nums[j] + nums[k];
                if (total > 0) {
                    k--;
                } else if (total<0) {
                    j++;
                } else {
                    res.add(Arrays.asList(nums[i], nums[j], nums[k]));
                    j++;
                    while (nums[j] == nums[j-1] && j < k) {
                        j++;
                    }
                }
            }
        }
        return res;        
    }
}
```
# 204. Count Primes
# Solution_Link : https://leetcode.com/problems/count-primes/submissions/1585100498/

# Code:
```
class Solution {
    public int countPrimes(int n) {
        if(n<=2) return 0;
        boolean[] composite=new boolean[n];
        int limit=(int)Math.sqrt(n);
        for(int i=2;i<=limit;i++){
            if(composite[i]==false){
                for(int j=i*i;j<n;j+=i){
                    composite[j]=true;
                }
            }
        }
        int count=0;
        for(int i=2;i<n;i++){
            if(composite[i]==false){
                count++;
            }
        }
        return count;
    }
}
```
# 41. First Missing Positive
# Solution_Link : https://leetcode.com/problems/first-missing-positive/submissions/1884705160

# Code:
```
class Solution {
    public int firstMissingPositive(int[] nums) {
        Arrays.sort(nums);
        int a=1;
        for(int i=0;i<nums.length;i++){
            if(a==nums[i]){
                a++;
            }
        }
     return a;
    }
}
```
# 4. Median of Two Sorted Arrays
# Solution_Link : https://leetcode.com/problems/median-of-two-sorted-arrays/submissions/1884543704

# Code :
```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int n1 = nums1.length;
        int n2 = nums2.length;
        int n = n1 + n2;
        int[] newarr = new int[n];
        int i=0, j=0, k=0;
        while (i<=n1 && j<=n2) {
            if (i == n1) {
                while(j<n2){ 
                newarr[k++] = nums2[j++];
                }
                break;
            } else if (j==n2) {
                while (i<n1) newarr[k++] = nums1[i++];
                break;
            }

            if (nums1[i] < nums2[j]) {
                newarr[k++] = nums1[i++];
            } else {
                newarr[k++] = nums2[j++];
            }
        }

        if (n%2==0){
        return (double)(newarr[n/2-1] + newarr[n/2])/2;
        }
        else return newarr[n/2];
    }
}
```
# Weekly Challenges:

# 455. Assign Cookies
# Solution_Link : https://leetcode.com/problems/assign-cookies/submissions/1900580572

# Code:
```
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int l = 0;
        int r = 0;
        while(r < g.length && l < s.length){
            if(g[r] <= s[l]){
                r = r + 1;
            }
            l = l + 1;
        }
        return r;
    }
}
```

# 575. Distribute Candies
# Solution_Link: https://leetcode.com/problems/distribute-candies/submissions/1587142824

# Code:
```
class Solution {
    public int distributeCandies(int[] candyType) {
        HashSet<Integer> set=new HashSet<>();
        for(int i=0;i<candyType.length;i++){
            set.add(candyType[i]);
        }
        if(set.size()>candyType.length/2){
            return candyType.length/2;
        }
        return set.size();
    }
}
```

# 992. Subarrays with K Different Integers
# Solution_Link : https://leetcode.com/problems/subarrays-with-k-different-integers/submissions/1740487967

# Code:
```
class Solution {
    public int subarraysWithKDistinct(int[] nums, int k) {
        return countsubarray(nums, k) - countsubarray(nums, k - 1);
    }

    public int countsubarray(int[] nums, int k) {
        int left = 0, right = 0, count = 0;
        HashMap<Integer, Integer> map = new HashMap<>();

        while (right < nums.length) {
            map.put(nums[right], map.getOrDefault(nums[right], 0) + 1);

            while (map.size() > k) {
                map.put(nums[left], map.get(nums[left]) - 1);
                if (map.get(nums[left]) == 0) {
                    map.remove(nums[left]);
                }
                left++;
            }

            count += (right - left + 1);
            right++;
        }

        return count;
    }
}
```
