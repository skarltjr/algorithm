```
package algo;


/**
 *
 */
class Solution {
    static int answer = 0;
    static boolean[] visited;

    public int solution(int n, int[][] computers) {
        visited = new boolean[n];
        for (int i = 0; i < n; i++) {
            if (visited[i] == false) {
                answer++;
                dfs(i,computers);
            }
        }

        return answer;
    }

    private void dfs(int start, int[][] computers) {
        for (int i = 0; i < computers.length; i++) { // computers.length == n
            if (computers[start][i] == 1 && visited[i] == false) {
                visited[i] = true;
                dfs(i, computers);
            }
        }
    }
}
```
