```
package algo;


/**
 * 7 6 5 8 3 5 9 1을 정렬해보자
 * 병합 정렬
 * 퀵 소트와 마찬가지로 분할정복★
 * O(n * logn)
 * <p>
 * 1) 7 6 5 8 3 5 9 1
 * 2) 67 | 58 | 35 | 91
 * 3) 5678 | 1359
 * 4) 13556789
 * <p>
 * 이미 정렬이 된 상태의 블럭을 합쳐서 새롭게 정렬한다
 */

public class Main {
    static int sorted[] = new int[8];    // 매 번 배열을 할당해서 사용하지않도록

    public static void merge(int[] ints,int left,int middle,int right) {
        /** 4. 가장 중요한 병합의 원리
         *  ex) 2개 2개 블럭을 병합한다고 할 때
         *
         *  i         j
         *  ㅁ ㅁ     ㅁ ㅁ
         *
         *  k
         *  ㅁㅁㅁㅁ
         *
         *  i와 j를 비교해서 작은 값을 k에
         *
         *  -----
         *
         *  다음 비교
         *  i            j
         *  ㅁ ㅁ     ㅁ ㅁ
         *
         *    k
         *  ㅁㅁㅁㅁ
         *
         * ----- 동일하게
         *
         *     i      j
         *  ㅁ ㅁ     ㅁ ㅁ
         *
         *      k
         *  ㅁㅁㅁㅁ
         *
         *
         * 중요한 것은 이전 블럭이 이미 정렬된 상태를 가정한다는 것 ★
         * 예를들어 2개 2개 블럭을 병합할 때 4번을 통해 이미 각각 2개 블럭은 모두 정렬된 상태라고 생각한다 그러기때문에 2개의 블럭을 i j로 비교할 수 있는 것
         *  */

        int i = left;
        int j = middle + 1;
        int k = left; // 당연히 k는 left 왼쪽블럭이랑 시작이 같으니

        /** 5. 지금 상황을 생각해보자 - 다 쪼개져서 1개 1개.... 블럭인 상태
         *  이 블럭들을 비교해서 새로운 2개짜리 블럭에 정렬시켜야한다*/

        while (i <= middle && j <= right) {  // ㅁ ㅁ ㅁ ㅁ 4개 블럭이면 middle => (0 + 3) / 1    | right = 3

            // 4번 과정 진행
            if (ints[i] <= ints[j]) {
                sorted[k] = ints[i];
                i++;
                k++;
            } else {
                sorted[k] = ints[j];
                j++;
                k++;
            }
        }

        /** 6. 마지막으로   ex) 5 8   |  1 2 라는 블럭을 ㅁㅁㅁㅁ에 정렬했다고 치자
         * 그럼 1 2 ㅁ ㅁ 안데 j는 이미 루프를 다 돈 상태고 i는 아직 5 8 이 남았다
         * 여기서 ★ 각 블럭은 이미 정렬된 상태고 따라서 남은 애들을 그냥 sorted[]에 삽입시켜주면 된다
         *
         * 참고로 6번 경우가 발생하는 경우는 i,j둘 중 하나는 이미 다 루프를 돈 상태다 ★
         * */

        if (i > middle) { // ㅁㅁ | ㅁㅁ  중 왼쪽 블럭 - i는 루프를 다 돈 상태
            for (int l = j; l <= right; l++) {
                sorted[k] = ints[l];
                k++;
            }
        } else {  // j가 루프를 다 돈 상태
            for (int l = i; l <= middle; l++) {
                sorted[k]=ints[l];
                k++;
            }
        }

        // 정렬한 sorted를 ints에 넣어준다
        for (int l = left; l <= right; l++) {
            ints[l] = sorted[l];
        }
    }

    public static void mergeSort(int[] ints, int start, int end) {

        /** 1. 먼저 분할을 해야하는데 분할을 할 기준을 잡기위한 middle설정*/
        if (start < end) {
            int middle = (start + end) / 2; // 중앙설정

            /** 2. 아래 과정을통해 8 -> 4 -> 2 -> 1개의 블럭으로 쪼갠다*/
            mergeSort(ints, start, middle);  // 중앙기준 왼쪽
            mergeSort(ints, middle + 1, end); // 중앙기준 오른쪽

            /** 3. 합쳐야한다
             *  여기서 그러면 mergesort()를 재귀를 통해 반복해서 들어가고 마지막으론 1칸의 블럭씩으로 다 쪼개진 상태에서 merge출발할것이다
             *  1 + 1 => 2 / 2 + 2 => 4 ...
             */
            merge(ints,start,middle,end);
        }
    }

    public static void main(String[] args) {
        int array[] = {7, 6, 5, 8, 3, 5, 9, 1};
        mergeSort(array, 0, array.length - 1);
        for (int i : array) {
            System.out.println(i);
        }
    }
}

```
