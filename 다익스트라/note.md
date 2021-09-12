```
package algo;


/**
 * 다익스트라 - 최단 경로 탐색
 * 특징 : 하나의 정점에서 다른 모든 정점까지의 거리를 알 수있다.
 * */
public class Main {
    static int INF = 9999;
    static int[][] graph =
            {
                    {0, 2, 5, 1, INF, INF},
                    {2, 0, 3, 2, INF, INF},
                    {5, 3, 0, 3, 1, 5},
                    {1, 2, 3, 0, 1, INF},
                    {INF, INF, 1, 1, 0, 2},
                    {INF, INF, 5, INF, 2, 0}
            };
    static boolean visited[] = new boolean[6];
    static int dist[] = new int[6]; // 현재 노드에서 다른 모든 노드까지의 거리 -> 다음 노드 선택할 때 사용
    public static void main(String[] args) {
        dijkstra(0);
        for (int i = 0; i < 6; i++) {
            System.out.println(dist[i]);
        }
    }

    public static void dijkstra(int start) {
        // 시작지점에서 다른 모든 노드까지의 거리 dist로
        for (int i = 0; i < 6; i++) {
            dist[i] = graph[start][i];
        }
        visited[start] = true;
        for (int i = 0; i < 5; i++) { // 노드 n개 최단거리는 a - ㅁ - ㅁ - b n-1번 거치면 나온다
            int current = getNext(); // 다음껄로 넘어오고
            visited[current] = true;
            for (int j = 0; j < 6; j++) {  // j가 다음껄로 넘어온 현 위치에서 다른 모든 노드들
                if (!visited[j]) {
                    if (dist[j] > graph[current][j] + dist[current]) {
                        dist[j] = graph[current][j] + dist[current];
                    }
                }
            }
        }
    }

    public static int getNext() {
        int min = INF;
        int next = 0;
        for (int i = 0; i < 6; i++) {
            if (!visited[i] && min > dist[i]) {
                next = i;
                min = dist[i];
            }
        }
        return next;
    }

}


```
