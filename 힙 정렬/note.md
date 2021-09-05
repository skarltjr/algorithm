```
package algo;


/**
 * 힙 정렬
 * 이진트리의 구조로 먼저 모든 노드 ( 숫자 )를 이진트리에 삽입
 * 이 후 가장 중요한 ★ heapify
 * ex) 최대힙이라면 자식 노드 중 부모노드보다 큰 값이 있다면 위치를 수정하여 하위 트리 구조를
 * 맨 아래 말단노드부터 부모노드와의 크기를 비교한다.
 */

public class Main {
    static int[] heap = {7, 6, 5, 8, 3, 5, 9, 1, 6};

    public static void main(String[] args) {
        // 최대힙 구조를 구성
        for (int i = 1; i < heap.length; i++) { // 참고로 1/2하면 어차피 0으로 들어가니까
            int now = i;
            /** 1. 기본적인 힙을 구성한다.
             *  여기서 하고자 하는 것은 매번 새로운 노드를 추가할 때 마다 추가한 노드가 루트보다 크면 위로 올린다
             *  즉. 가장 노드를 추가할 때 마다 힙의 최대값을 초기화*/
            do {
                int root = (now - 1) / 2;
                if (heap[root] < heap[now]) {
                    int temp = heap[root];
                    heap[root] = heap[now];
                    heap[now] = temp;
                }
                now = root;
            } while (now != 0);
        }

        /** 2. 이제 최소힙을 구성하자
         * 가장 큰 값이 맨 위 루트 노드에 위치
         * 1) 이 값을 맨 마지막. 말단과 위치를 변경하여 가장 큰 값을 뒤로보내는 / 가장 작은 값이 맨위에있는 최소힙을 만든다
         * 2) 자식과 부모를 비교하여 힙을 구성   / 이진트리 - 자식 중 더 큰 값을 구하고 그 값을 부모와 비교하여 위치 조정
         * 또 올라가면서 힙을 구성 .... 1)부터 다시 반복 ... 최소힙
         * */
        for (int i = heap.length - 1; i >= 0; i--) {
            // 1) 가장 큰 값을 맨 뒤로 보낸다
            int temp = heap[0];
            heap[0] = heap[i];
            heap[i] = temp;
            // 2) 자식 - 부모 비교하여 큰 값을 찾고 위로 올린다
            int child = i;
            int root = 0;

            do {  /** 3. 사실상 가장 핵심부분 위에서부터 내려가면서 작은 최대힙을 구성 -> 큰 값을 계속 위로 올리고 -> 1)을 진행해서 결국 마지막으로 내린다 -> 최소힙*/
                child = root * 2 + 1;
                if (child < i-1 && heap[child] < heap[child + 1]) { // 오른쪽 자식이 더 크면 + 참고로 i-1까지인 이유는 바로 범위를 지정하되 앞에서 가장 큰 값을 맨 뒤로 보냈고 그 노드를 제외하고 계산을 고려한다
                    child++; // 오른쪽자식으로 관점을 이동
                }
                if (child < i && heap[root] < heap[child]) {
                    temp = heap[root];
                    heap[root] = heap[child];
                    heap[child] = temp;
                }
                root = child;
            } while (child < i);
        }

        for (int i : heap) {
            System.out.println(i);
        }
    }
}

```
