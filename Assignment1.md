# 121. Best Time to Buy and Sell Stock
## Question_Link : https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/

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
