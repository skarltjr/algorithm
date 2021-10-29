```
package algo;


import java.util.HashSet;
import java.util.Set;

/**
 * 만들 수 있는 모든 수를 만드는데 이 때 하나 만들 때 마다 소수인지를 판별해서 set에 추가 혹은 개수 추가
 * 11과 011은 같은 숫자로 취급합니다.
 * 
 * 실수 : 시간초과가 2개 발생했었다
 * 소수판별이 시간을 많이 잡아먹어서 set으로 중복숫자 제거 후 소수판별하는 로직으로 변경 -> ok
 */
class Solution {
    static int answer = 0;
    static Set<Integer> set = new HashSet<>();
    public int solution(String numbers) {
        boolean[] visited = new boolean[numbers.length()];
        dfs(0,numbers,"",visited);
        for (Integer integer : set) {
            if (isPrime(integer)) {
                answer++;
            }
        }
        return answer;
    }

    private void dfs(int depth,String numbers,String current,boolean[] visited) { // 가능한 모든 수 만들기
        if (depth == numbers.length()) {
            return;
        }

        String temp = current;
        for (int i = 0; i < numbers.length(); i++) {
            if (!visited[i]) {
                visited[i] = true;
                current += numbers.charAt(i);
                if (current.length() > 1 && current.charAt(0) == '0') {
                    current = current.substring(1, current.length());
                }
                int num = Integer.parseInt(current);
                set.add(num);

                dfs(depth + 1, numbers, current, visited);

                // 011일 때 0번에서 0번 visited true로 남으면 1 차례 때 0이 visited로 남아있어서 문제
                current = temp;
                visited[i] = false;
            }
        }

    }

    public boolean isPrime(int num) {  // 소수 확인
        int count = 0;
        for (int i = 2; i <= num; i++) {
            if (num % i == 0) {
                count++;
            }
        }
        if (count == 1) {
            return true;
        }
        return false;
    }
}
```
