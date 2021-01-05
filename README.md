# Find-minimum-number-of-coins-that-make-a-given-value
Find the minimum number of coins required to make n cents.  You can use standard American denominations, that is, 1¢, 5¢, 10¢, and 25¢.  For example, given n = 16, return 3 since we can make it with a 10¢, a 5¢, and a 1¢.  For example, given the array [0, 8, 4, 12, 2, 10, 6, 14, 1, 9, 5, 13, 3, 11, 7, 15], the longest increasing subsequence has length 6: it is 0, 2, 6, 9, 11, 15.

#include<bits/stdc++.h> 
using namespace std; 
  
// m is size of coins array (number of different coins) 
int minCoins(int coins[], int m, int V) 
{ 
   // base case 
   if (V == 0) return 0; 
  
   // Initialize result 
   int res = INT_MAX; 
  
   // Try every coin that has smaller value than V 
   for (int i=0; i<m; i++) 
   { 
     if (coins[i] <= V) 
     { 
         int sub_res = minCoins(coins, m, V-coins[i]); 
  
         // Check for INT_MAX to avoid overflow and see if 
         // result can minimized 
         if (sub_res != INT_MAX && sub_res + 1 < res) 
            res = sub_res + 1; 
     } 
   } 
   return res; 
} 
  
// Driver program to test above function 
int main() 
{ 
    int coins[] =  {9, 6, 5, 1}; 
    int m = sizeof(coins)/sizeof(coins[0]); 
    int V = 11; 
    cout << "Minimum coins required is "
         << minCoins(coins, m, V); 
    return 0; 
} 
