```
package algo;


import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;


/**
 * DFS 깊이 우선 탐색
 * 깊이를 따라 쭉 따라가고 끝을 만나면 이전 분기점에서 다른길로
 * */
public class Main {
    // 2차원 arraylist 헷갈렸었다
    static ArrayList<Integer>[] node = new ArrayList[8];
    static int[] visited = new int[8];
    static void dfs(int start) {
        if (visited[start] != 0) {
            return;
        }
        visited[start] = 1;
        System.out.println(start);
        for (int i = 0; i < node[start].size(); i++) {
            int next = node[start].get(i);
            dfs(next);
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


        dfs(1);

    }
}

```
