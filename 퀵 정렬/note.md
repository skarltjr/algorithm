```
package algo;



/**
 * 1 10 5 8 7 6 4 3 2 9
 * 퀵 정렬
 * O(n * logn)
 * 특정한 값(pivot)을 기준으로 큰 수와 작은 수를 나누자
 * 피벗 기준 큰 값은 왼쪽부터
 * 피벗 기준 작은 값은 오른쪽부터
 * -------------------
 *
 * 1 10 5 8 7 6 4 3 2 9 을 정렬하고자 한다.
 * 피벗을 1로 잡은 경우 = 1을 기준으로★ 1보다 작은수는 오른쪽에서부터 큰 수는 왼쪽부터★ 찾는다 ★ - 그럼 생각해보면 두 개의 인덱스가 필요할거라 예상가능
 * 이 때 1보다 큰 수는 왼쪽부터 찾으면 1 다음 바로 10을 찾을 수 있다  / 1보다 작은 수는 왼쪽부터 찾아도 존재하지 않는다.
 * 그러면 왼쪽부터 큰 값을 찾는 인덱스는 10에서 바로찾았고 10에 위치한다.
 * 반대로 오른쪽부터 1보다 작은 값을 찾는 인덱스는 없으니까 1까지 이동하여 위치
 * 이 때 작은 값의 인덱스가 큰 값의 인덱스보다 작으므로 피벗과 작은값의 위치를 변경 = 피벗과 작은값 둘 다 1에 위치 = 그대로
 * 그런데 이 때 피벗의 위치 자체는 그대로이지만 피벗을 움직였기 때문에 다음 피벗을 선택
 * -------------------
 *
 * 1 10 5 8 7 6 4 3 2 9
 * 피벗을 설정 pivot = 10
 * 현재의 10 위치 기준으로 10보다 큰 값을 왼쪽에서부터 / 작은값을 오른쪽에서부터 찾는다
 * 큰 값은 없으니 9까지 인덱스가 이동할것이고 / 작은 값은 오른쪽에서부터 찾으면 바로 9를 찾을 수 있다.
 * 이 때 작은 값의 인덱스가 큰 값의 인덱스보다 작거나 같으므로 피벗과 작은값의 위치를 변경  = 피벗 10과 작은값 9를 변경
 * 1 9 5 8 7 6 4 3 2 10 으로 정렬이 된다
 * -------------------
 *
 * 위에서도 피벗을 움직였으니 다시 선택 -> 원래 피벗위치 ++
 * 1 9 5 8 7 6 4 3 2 10에서 피벗 5를 기준으로
 *
 * */
public class Main {
     public static void quicksort(int[] ints,int start,int end) {
        if (start >= end) {
            return;
        }
        int pivot = start;

        // +1하는 이유는 굳이 자기자신부터 시작할 필요없이 나 다음 놈부터 시작하면 빠르니까
        int left = start+1; // 피벗보다 큰놈을 찾기위한
        int right = end;    // 피벗보다 작은놈

        while (left <= right) { // 엇갈릴때까지
            while (left <= end && ints[left] <= ints[pivot]) {
                left++;
            }
            while (right > start && ints[right] >= ints[pivot]) {
                right--;
            }

            if (left > right) { // ex) 작은놈과 큰놈이 엇갈린 상태 -->> pivot _ _ 작은놈(오른쪽부터 출발한) _ _ 큰놈  -->> 피벗과 작은놈을 위치변경
                int temp = ints[right];
                ints[right] = ints[pivot];
                ints[pivot] = temp;
            } else {
                // ex) 엇갈리지 않은 상태 pivot _ _ 큰놈 _ _ 작은놈 -->> 피벗은 그대로두고 큰 작은 위치변경
                // or ex) 큰놈 _ _ pivot _ _ 작은놈
                int temp = ints[right];
                ints[right] = ints[left];
                ints[left] = temp;
            }

            // left > right  | else 두 조건 모두 결국 작은놈 right는 pivot 혹은 큰놈과 위치가 변경된다
            // 무조건 위치가 변경되는 right기준으로 양 쪽을 다시 quick sort

            quicksort(ints, start, right - 1);
            quicksort(ints,right+1,end);
        }
    }
    public static void main(String[] args) {
        int[] ints = {1, 10, 5, 8, 7, 6, 4, 3, 2, 9};

        quicksort(ints,0,ints.length-1);
        for (int anInt : ints) {
            System.out.println(anInt);
        }
    }
}


```
