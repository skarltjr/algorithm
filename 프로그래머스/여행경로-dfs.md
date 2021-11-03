```
package algo;


import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

/**
 * 항상 "ICN" 공항에서 출발합니다.
 * ICN으로 출발하는 모든 경우를 만들고
 * 이를 sort해서
 * 맨 처음걸return
 */
class Solution {
    static List<String> list = new ArrayList<>();
    public String[] solution(String[][] tickets) {
        boolean[] visited = new boolean[tickets.length];

        // 가능한 모든 순회 경우를 만들고
        for (int i = 0; i < tickets.length; i++) {
            String start = "ICN";
            String result = start;
            if (tickets[i][0].equals(start)) {
                int count = 0;
                dfs(start,result,count,tickets,visited);
            }
        }

        // 정렬 후
        Collections.sort(list);

        // 가장 첫번째껄 답으로
        String ans = list.get(0);
        String[] answer = new String[ans.length() / 3];
        int i = 0;
        int len = 0;
        while (len < ans.length()) {
            answer[i] = ans.substring(len, len + 3);
            i++;
            len += 3;
        }

        return answer;
    }

    private void dfs(String start, String result, int count, String[][] tickets, boolean[] visited) {
        if (count == tickets.length) {
            list.add(result);
            return;
        }

        String origin = result;
        for (int i = 0; i < tickets.length; i++) {
            if (visited[i] == false && tickets[i][0].equals(start)) {
                visited[i] = true;
                String next = tickets[i][1];
                result += next;
                dfs(next,result,count+1,tickets,visited);
                visited[i] = false;
                result = origin;
            }
        }
    }

}
```
