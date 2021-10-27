```

import java.util.Arrays;


/**
 * n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index
 * h는 citations내의 인자가 아니라 단순한 인용 횟수로 봐야한다. citations안에 없는 값일 수 있다
 *
 * */
class Solution {
    public int solution(int[] citations) {
        
        Arrays.sort(citations);
        int max = 0;

        // h=6이면 length는 6이상이다
        // h=100dlaus  length는 100 이상
        for (int i = 1; i <= citations.length; i++) {
            int count = 0;
            for (int j = 0; j < citations.length; j++) {
                if (citations[j] >= i) {
                    count++;
                }
            }

            if (count >= i) {
                max = i;
            }
        }


        return max;
    }
}
```
