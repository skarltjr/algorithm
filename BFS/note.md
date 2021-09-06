```
package algo;


import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;


/**
 * BFS 너비 우선 탐색
 * 너비를 우선하여 탐색
 * 최단 경로를 찾아준다는 점에서 - 최단길이를 보장해야할 때 사용
 * 큐를 통한 활용
 * */
public class Main {
    // 2차원 arraylist 헷갈렸었다
    static ArrayList<Integer>[] node = new ArrayList[8];
    static int[] visited = new int[8];
    static void bfs(int start) {
        Queue<Integer> q = new LinkedList<>();
        q.add(start);
        visited[start] = 1; // true
        while (!q.isEmpty()) {
            int now = q.peek();
            q.poll();
            System.out.println(now);;
            for (int i = 0; i < node[now].size(); i++) {
                int next = node[now].get(i);
                if (visited[next] == 0) {
                    q.add(next);
                    visited[next] = 1;
                }
            }
        }

    }
    public static void main(String[] args) {
        for (int i = 1; i <= 7; i++) {
            node[i] = new ArrayList<>();
        }
        node[1].add(2);
        node[1].add(3);

        node[2].add(1);
        node[2].add(3);
        node[2].add(4);
        node[2].add(5);

        node[3].add(1);
        node[3].add(2);
        node[3].add(6);
        node[3].add(7);

        node[4].add(2);
        node[4].add(5);

        node[5].add(2);
        node[5].add(4);

        node[6].add(3);
        node[6].add(7);

        node[7].add(3);
        node[7].add(6);


        bfs(1);

    }
}

```
