```
package algo;



/**
 * 1 10 5 8 7 6 4 3 2 9
 * 각 숫자를 적절한 위치에 삽입하면 ?
 * O(n^2)
 * 그럼 이걸 왜 쓰나 똑같은 효율인데?
 * 거의 정렬된 상태라면 매우 빠르기 때문
 *
 * 1 10 5 8 7 6 4 3 2 9을 보자
 * 삽입정렬은 내 앞이 이미 정렬이 되어있다는 것을 가정
 * 1부터 보면 1은 앞에 더 이상 들어갈 공간이 없으므로 skip
 * _ 1 _     10 - 10은 앞에 들어갈 공간이 2개가 있는데 1보다 크기 때문에 그대로 위치
 * _ 1 _ 10 _ 5    - 5는 앞에 들어갈 공간이 총 3개 1보다 크고 10보다 작기 때문에 1과 10 사이로 삽입
 * -> 1 5 10 ....
 *
 * --------------
 * 
 * 내 생각은 현재 1 5 10 까지 정렬 후 8의 차례일 때  / 나의 위치 = 8
 * 8을 움직이는데 이 때 현재 나의 앞에 녀석과 비교하고 나보다 크면 (10이니까) 위치를 바꾼다 -> 1 5 8 10
 * 이 후 나의 위치가 한 칸 앞으로 변경되었음을 인지 ★ index--
 * 다시 한 칸 앞으로 온 나의 위치에서 동일한 로직 반복 - 앞 녀석과 비교
 * 그런데 이 때 5는 나보다 작으니 나의 위치는 바로 현재 여기. 반복종료
 * */
public class Main {
    public static void main(String[] args) {
        int[] ints = {1, 10, 5, 8, 7, 6, 4, 3, 2, 9};
        for (int i = 0; i < 10; i++) {  
            int j = i; // 현재 나의 위치
            while (j > 0 && ints[j - 1] > ints[j]) { // j >=0이면 당연히 0보다 앞에 녀석없으니 index에러
                int  temp = ints[j-1];
                ints[j-1] = ints[j];
                ints[j] = temp;
                j--; //매우 중요 ★
            }
        }
        for (int anInt : ints) {
            System.out.println(anInt);
        }

    }
}

```
