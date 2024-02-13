## [PCCE 기출문제] 9번 / 이웃한 칸
- https://school.programmers.co.kr/learn/courses/30/lessons/250121
---

### Point


---

```
import java.util.*;
class Solution {
    public int[][] solution(int[][] data, String ext, int val_ext, String sort_by) {
        int[][] answer = {};
        
        HashMap<String, Integer> dataType = new HashMap<>();
        dataType.put("code",0);
        dataType.put("date",1);
        dataType.put("maximum",2);
        dataType.put("remain",3);
        
        // 가공 조건에 맞게 필터링
        List<int[]> filterData = new ArrayList<>();
        for(int i=0; i<data.length; i++){
            if(data[i][dataType.get(ext)] < val_ext){
                filterData.add(data[i]);
            }
        }
        
        // 정렬 조건에 맞게 정렬
        filterData.sort(Comparator.comparingInt(arr -> arr[dataType.get(sort_by)]));

        // 정수형 배열로 변환
        answer = new int[filterData.size()][4];
        for(int i=0; i<filterData.size(); i++){
            answer[i] = filterData.get(i);
        }
        
        return answer;
    }
    

}
```