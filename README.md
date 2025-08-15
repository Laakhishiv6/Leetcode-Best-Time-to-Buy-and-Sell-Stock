# Leetcode-Best-Time-to-Buy-and-Sell-Stock
# Description
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
# Solution
This approach uses two pointers:

l → Buy day

r → Sell day

We check if selling on day r yields profit compared to buying on day l:

If yes, calculate and update max_profit.

If no (price at r is lower), move l to r (new buy day).
Example 1:

Input: prices = [7,1,5,3,6,4]

Output: 5

Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.

Example 2:

Input: prices = [7,6,4,3,1]

Output: 0

Explanation: In this case, no transactions are done and the max profit = 0.
 
# Algorithm
1. Initialize l = 0 (buy day), r = 1 (sell day), and maxp = 0.
2. While r is within the array: If prices[l] < prices[r]: Calculate profit = prices[r] - prices[l].
3. Update maxp = max(maxp, profit).
4. Else: Move l to r (new buy day).
5. Increment r to check next sell day.
6. Return maxp.
# Code
class Solution:

    def maxProfit(self, prices: List[int]) -> int:
        l,r=0,1
        maxp=0
        for i in range(len(prices)-1):
            if prices[l]<prices[r]:
                prof=prices[r]-prices[l]
                maxp=max(maxp,prof)
            else:
                l=r
            r+=1
      

        return maxp
        
# Complexity
Time Complexity:

We traverse the list once, doing O(1) work for each element (comparisons and assignments).

No nested loops or sorting.

Time Complexity = O(n)


Space Complexity:

We only store a few variables: min_price, max_profit, and a loop variable.

No extra data structures that grow with input size.

Space Complexity = O(1)
