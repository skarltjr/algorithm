```
package algo;


/**
 * Union - Find / 합집합 찾기 ★
 * 1) Union
 * ex) 각 노드는 우선 자기 자신을 부모로 갖는다      1 =1을  2 =2를 부모로...
 * 만약 1과 2가 연결되었다면 작은 쪽을 부모로 갖는다. 1의 부모는 그대로 1  / 2의 부모는 1  => 1과 2는 연결된 상태
 * 추가로 2와 3이 연결된 상태라면                  2의 부모는 그대로 1 / 3의 부모는 2 => 2와 3은 연결된 상태
 *
 * 2) Find
 * 그럼 1,2,3,4가 서로 같은 집합인지 찾으려면?
 * - 각 숫자의 부모를 찾는다
 * - 쭉 부모를 찾아 따라가다 부모가 자기자신이라면 stop
 * 1의 부모는 = 1
 * 2의 부모는 = 1
 * 3의 부모는 2 / 2의부모는 1 = 1
 * - 1,2,3은 최종적으로 부모가 같으니 같은 집합
 * 4의 부모는 4
 * 1,2,3 /// 4
 * */
public class Main {

    static int[] parent = new int[9]; // 1부터 시작하기 위해

    static public void union(int first, int second) {
        // 여기 들어온다는건 first와 second 둘을 연결하겠다는 뜻
        int a = getParent(first);
        int b = getParent(second);
        if (a <= b) {
            parent[b] = a;
        } else {
            parent[a] = b;
        }
    }

    static public int getParent(int target) {
        // 부모를 찾는
        if (parent[target] == target) {
            return target;
        } else {
            return getParent(parent[target]);
        }
    }

    static public boolean find(int first, int second) {
        // 둘이 합집합인가?를 찾는
        int a = getParent(first);
        int b = getParent(second);
        if (a == b) {
            return true;
        } else {
            return false;
        }
    }
    public static void main(String[] args) {
        for (int i = 1; i < parent.length; i++) {
            parent[i] = i;
        }

        union(1, 2);
        union(2, 3);
        union(3, 4);

        // 그럼 1,2,3,4 // 5,6,7,8 두 집합으로 나뉠 것

        union(5, 6);
        union(6, 7);
        union(7, 8);

        System.out.println("1,4는 연결되어있나?" + find(1, 4));
        System.out.println("5,8은 연결되어있나?" + find(5, 8));
        //true

        System.out.println("1,5는 연결되어있나?" + find(1, 5));
        //false
        union(1,5);
        System.out.println("1,5는 연결되어있나?" + find(1, 5));
        //true

    }
}

```
