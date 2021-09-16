```
package algo;


import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;
import java.util.Queue;

/**
 * 위상 정렬
 * ★ 사이클이 없어야하며
 * ★ 시작점이 존재해야한다 = 사이클이 없어야한다
 * ★ 진입차수를 고려해라
 *
 * 1. 진입차수가 0인 지점을 큐에 삽입
 * 2. 큐에서 원소를 꺼내고 이와 연결된 모든 간선 제거
 * 3. 간선 제거 후 다시 큐에서 이번에 진입차수가 0이 된 애를 꺼낸다
 * 4. 큐가 빌 때까지 반복 / 만약 모든 원소를 방문하기 전에 큐가 빈다면 사이클이 존재하는 것
 * 5. 모든 원소를 방문했다면 위상정렬의 결과
 * */
public class Main {

    static int[] inDegree = new int[8]; // 진입 차수
    static ArrayList<Integer>[] node = new ArrayList[8]; // 연결 간선

    private static void topologySort() {
        List<Integer> result = new ArrayList<>();

        Queue<Integer> q = new LinkedList<>();
        for (int i = 1; i < 8; i++) {
            if (inDegree[i] == 0) {
                q.add(i);
            }
        }

        for (int i = 1; i < 8; i++) {
            if (q.isEmpty()) {
                System.out.println("사이클 존재");
                return;
            }

            int poll = q.poll();
            result.add(poll);
            for (int j = 0; j < node[poll].size(); j++) {
                int target = node[poll].get(j);
                if (--inDegree[target] == 0) { // 간선을 제거
                    q.add(target);
                }
            }
        }
        for (Integer integer : result) {
            System.out.println(integer);
        }
    }

    public static void main(String[] args) {
        // 예시는 총 1~7 노드

        for (int i = 1; i < 8; i++) { // 1부터 시작
            node[i] = new ArrayList<>();
        }

        // 1번 노드와 2번 노드 연결
        node[1].add(2);
        // 2번 노드는 이제 진입차수가 1 증가
        inDegree[2]++;

        node[1].add(5);
        inDegree[5]++;

        node[2].add(3);
        inDegree[3]++;

        node[3].add(4);
        inDegree[4]++;

        node[4].add(6);
        inDegree[6]++;

        node[5].add(6);
        inDegree[6]++;

        node[6].add(7);
        inDegree[7]++;

        topologySort();
    }

}



```
