```
package algo;

/**
 * 플로이드 와샬 - 최단 경로 알고리즘
 * ★ 모든 정점 -> 모든 정점
 * 다익스트라는 하나의 시작에서 모든 정점까지의
 *
 * */

public class Main {
    static int INF = 9999;
    static int[][] graph = {
            {0, 5, INF, 8},
            {7, 0, 9, INF},
            {2, INF, 0, 4},
            {INF, INF, 3, 0}
    };

    public static void floydWarshall() {
        for (int i = 0; i < 4; i++) {
            for (int j = 0; j < 4; j++) {
                for (int k = 0; k < 4; k++) {
                    if (graph[i][k] > graph[i][j] + graph[j][k]) {
                        graph[i][k] = graph[i][j] + graph[j][k];
                    }
                }
            }
        }
    }
    public static void main(String[] args) {
        floydWarshall();
        for (int i = 0; i < 4; i++) {
            for (int j = 0; j < 4; j++) {
                if (j == 3) {
                    System.out.println(graph[i][j]);
                    continue;
                }
                System.out.printf("%d ",graph[i][j]);
            }
        }
    }

}


```
