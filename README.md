class Solution {
    public boolean isHappy(int n) {
        int slow = n;
        int fast = getNext(n);
        
        // 如果快指針先到 1，或者快慢指針相遇（代表有循環），就停止
        while (fast != 1 && slow != fast) {
            slow = getNext(slow);         // 走 1 步
            fast = getNext(getNext(fast)); // 走 2 步
        }
        
        // 只有在快指針停在 1 時，才是快樂數
        return fast == 1;
    }

    // 輔助函式：計算位數平方和
    private int getNext(int n) {
        int totalSum = 0;
        while (n > 0) {
            int d = n % 10;
            totalSum += d * d;
            n /= 10;
        }
        return totalSum;
    }
}
