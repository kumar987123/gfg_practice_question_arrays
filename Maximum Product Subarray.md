## Maximum Product Subarray

Given an array Arr[] that contains N integers (may be positive, negative or zero). Find the product of the maximum product subarray.

Example 1:

Input:
N = 5
Arr[] = {6, -3, -10, 0, 2}
Output: 180
Explanation: Subarray with maximum product
is [6, -3, -10] which gives product as 180.


Example 2:

Input:
N = 6
Arr[] = {2, 3, 4, 5, -1, 0}
Output: 120
Explanation: Subarray with maximum product
is [2, 3, 4, 5] which gives product as 120.

```java
class Solution {
    // Function to find maximum product subarray
    long maxProduct(int[] arr, int n) {
        // code here
        
        long prefix = 1;
        long suffix = 1;
        long ans = Integer.MIN_VALUE;
        
        for(int i=0; i<n; i++){
            if(prefix == 0){
                prefix = 1;
            }
            
            if(suffix == 0){
                suffix = 1;
            }
            
            prefix = prefix * arr[i];
            suffix = suffix * arr[n-i-1];
            
            ans = Math.max(ans, Math.max(prefix, suffix));
        }
        
        return ans;
    }
}
