## [PCCE 기출문제] 9번 / 이웃한 칸
- https://school.programmers.co.kr/learn/courses/30/lessons/250125
---

### Point


---

```
class Solution {
    public int solution(String[][] board, int h, int w) {
        int answer = 0;
        
        // 1.
        int n = board.length;
        // 2.
        int count = 0;
        // 3.
        int[] dh = {0,1,-1,0};
        int[] dw = {1,0,0,-1};
        
        // 4.
        for(int i=0; i<4; i++){
            // 4-1
            int h_check = h + dh[i];
            int w_check = w + dw[i];
            
            // 4-2
            if((h_check >= 0 && h_check < n) && (w_check >= 0 && w_check <n)){
                // 4-2-a
                if(board[h][w].equals(board[h_check][w_check])) count++;
            }
        }
        
        answer = count;
        
        return answer;
    }
}
```