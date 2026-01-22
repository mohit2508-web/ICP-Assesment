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
