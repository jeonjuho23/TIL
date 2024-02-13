## [PCCP 기출문제] 1번 / 붕대 감기
- https://school.programmers.co.kr/learn/courses/30/lessons/250137
---

### Point

먼저, 기능하는 것들을 나누었습니다.
공격, 붕대감기(치료), 죽음으로 나우어서 각 시간에 체력을 계산하도록 했습니다.
또한, 공격할때만 체력을 계산하면 되므로 시간을 하나씩 보내는 것보다 공격하는 시간에 맞추어 체력을 감소시키고 다음 공격까지 체력을 회복하였습니다.


---

```
class Solution {
    public int solution(int[] bandage, int health, int[][] attacks) {
        int answer = 0;
        
        int t = bandage[0];
        int x = bandage[1];
        int y = bandage[2];
        // 연속 성공 카운트
        int bandageCount = 0;
        int time = 0;
        int maxHealth = health;
        
        for(int attackCount=0; attackCount<attacks.length; attackCount++){
            
            // 공격
            health -= attacks[attackCount][1];
            
            // 죽음
            if(health <= 0){
                return -1;
            }
            
            time = attacks[attackCount][0] + 1;
            
            
            // 회복
            // 마지막 공격은 회복하지 않음
            if(attackCount >= attacks.length-1){
                break;
            }
            int bandageTime = 0;
            for(int healTime=time; healTime<attacks[attackCount+1][0]; healTime++){
                // 붕대감기
                health += x;
                bandageTime++;
                
                // 붕대감기 성공
                if(bandageTime%t == 0){
                    health += y;
                }
            }
            
            
            // 최대 체력을 넘지 않음
            if(maxHealth < health){
                health = maxHealth;
            }
            
        }
        
        answer = health;
        
        return answer;
    }
}
```