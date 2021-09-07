```
package algo;


import java.util.ArrayList;
import java.util.PriorityQueue;

/**
 * 크루스칼 알고리즘 Kruskal
 * 가장 적은 비용으로 모든 노드를 연결하는 알고리즘
 * 최소 비용 신장 트리 ★
 * 여러 노드가 존재하고 이 노드들을 잇는 여러개의 link가 존재하는 상황
 * 이 중 최소 비용(최소 가중치 합)으로 모든 노드를 연결하는 방법을 찾을 때 사용
 *
 * - 아이디어 : 거리(가중치)가 짧은 순서대로 그래프에 포함시키면?
 * - 모든 link를 오름차순으로 정렬 후 비용이 적은순으로 그래프에 하나씩 포함시키자
 *
 * ★ 이 때 가장 중요한 것은 cycle이 발생하지 않도록 -> union find
 * 1. 오름차순으로 link들 정렬
 * 2. cycle을 먼저 확인 / cycle이 발생하면 skip 후 그 다음 최소 비용 간선 선택
 * 3. cycle이 발생하지 않으면 link를 그래프에 추가
 *
 * ★ 애초에 모든 노드들은 연결하는 최소 간선 개수는 node-1개
 * = 사이클이 발생할 수 없다.
 *
 * ★ Comparable & 우선순위 큐를 사용하자!
 * */

public class Main {
    static public int[] parent = new int[8];

    static public void union(int first,int second) {
        int a = getParent(first);
        int b = getParent(second);
        if (a < b) {
            parent[b] = a;
        } else {
            parent[a] = b;
        }
    }
    static public int getParent(int target) {
        if (parent[target] == target) {
            return target;
        } else {
            return getParent(parent[target]);
        }
    }

    static public boolean find(int first,int second) {
        int a = getParent(first);
        int b = getParent(second);
        if (a == b) {
            return true;
        } else {
            return false;
        }
    }
    public static void main(String[] args) {
        // 1. 우선순위 큐를 통해 edge삽입 - comparable 구현을 통한 자동정렬
        PriorityQueue<Edge> edges = new PriorityQueue<>();

        edges.add(new Edge(1, 7, 12));
        edges.add(new Edge(1, 4, 28));
        edges.add(new Edge(1, 2, 67));
        edges.add(new Edge(1, 5, 17));

        edges.add(new Edge(2, 4, 24));
        edges.add(new Edge(2, 5, 62));

        edges.add(new Edge(3, 5, 20));
        edges.add(new Edge(3, 6, 37));

        edges.add(new Edge(4, 7, 13));
        edges.add(new Edge(5, 6, 45));

        edges.add(new Edge(5, 7, 73));

        // 부모 자기자신으로 초기화
        for (int i = 1; i < parent.length; i++) {
            parent[i] = i;
        }

        // 2. 작은 것 부터 그래프에 포함
        int sum = 0;
        while (!edges.isEmpty()) {
            Edge poll = edges.poll();
        // 3. 이 때 cycle 발생여부 체크먼저!!
            if (!find(poll.node[0], poll.node[1])) {
                sum += poll.dist;
                union(poll.node[0], poll.node[1]);
            }
        }
        // 4. 구하고자 하는것이 모든 노드를 연결하기 위한 / 최소 비용 /이라는걸 다시 상기하기\

        System.out.println(sum);
    }
}

class Edge implements Comparable<Edge>{
    public int node[] = new int[2];
    public int dist;

    public Edge(int from,int to, int dist) {
        node[0] = from;
        node[1] = to;
        this.dist = dist;
    }

    @Override
    public int compareTo(Edge o) {
        return o.dist > this.dist ? -1 : 1; // 참고로 음수면 두 개의 자리를 변경 근데 큐를 사용하고 오름차순으로 할거니까 
    }
}

```
