```
package algo;


/**
 * 다이나믹 프로그래밍  dp
 * 하나의 문제를 한 번만 푼다
 * 이 때 이전 값을 기억해두지 않으면 하나의 문제를 한 번만 풀지 않고 반복하여 비효율적 - memoization
 * 규칙성을 찾아 점화식을 만들자
 * */



/**
 * 1.
 * 2×n 크기의 직사각형을 1×2, 2×1 타일로 채우는 방법의 수를 구하는 프로그램을 작성하시오.
 * ㅁ       ㅁㅁ
 * ㅁ
 *
 * 2x1 ㅁ
 *     ㅁ
 *
 * 2x2  ㅁㅁ   1. ㅁ  2개   2. ㅁㅁ  위 아래로 개
 *      ㅁㅁ      ㅁ
 *
 * 2x3 3가지 방법 = (3-2) + (3-1)번쨰
 *
 * 2x4 5가지 = (4-2) + (4 -1)번째
 *
 *
 * 결국 n이 어떤 값이든
 * 1.
 *  (n-1) + ㅁ
 *          ㅁ
 *
 *          or
 *  2.
 *  (n-2) + ㅁㅁ   ㅁㅁ 짜리 위아래로 2개 이 경우밖에 없다  ㅁ 짜리 2개는 1번에 결국 포함되는 내용
 *          ㅁㅁ                                      ㅁ
 *
 *  즉 2 경우 밖에 없다는 것
 *  = 맨 뒤가 ㅁ 인 경우   a[n-1]에 ㅁ 추가하는 것일 뿐 따라서 가지 수는 a[n-1]랑 같다
 *           ㅁ                   ㅁ
 *  = 맨 뒤가 ㅁㅁ 인 경우 a[n-2]에 ㅁㅁ 추가하는 것 ....               a[n-2]랑 같다
 *           ㅁㅁ                 ㅁㅁ
 *  =>  경우의 수는 결국  a[n] = a[n-1] + a[n-2]가 된다
* */
public class Main {

    static int[] result = new int[100];
    public static void main(String[] args) {

    }

    public static int dp(int x) {
        if (x == 1) {
            return 1;
        }
        if (x == 2) {
            return 2;
        }
        if (result[x] != 0) {
            return result[x];
        }
        return result[x] = dp(x - 1) + dp(x - 2);
    }
}


```

------

```
package algo;


/**
 * 다이나믹 프로그래밍  dp
 * 하나의 문제를 한 번만 푼다
 * 이 때 이전 값을 기억해두지 않으면 하나의 문제를 한 번만 풀지 않고 반복하여 비효율적 - memoization
 * 규칙성을 찾아 점화식을 만들자
 * */



/**
 * 2×n 직사각형을 1×2, 2×1과 2×2 타일로 채우는 방법의 수를 구하는 프로그램을 작성하시오.
 * 규칙성을 찾고
 * 앞에것을 기억해라
 *
 * 결국
 * 1.
 * n-1 + ㅁ
 *       ㅁ
 * 2.                   ->    2x1 위아래   /  2x2 통짜 1개 
 * n-2 + ㅁㅁ                 ㅁㅁ           ㅁㅁ
 *       ㅁㅁ                 ㅁㅁ           ㅁㅁ
 *
 * 3가지의 경우만 존재한다
 * n = 1  1가지 ㅁ
 *             ㅁ
 * n = 2  ㅁ|ㅁ   ㅁㅁ 2x1 위아래   ㅁㅁ 2x2 1개  ==> 총 3가지
 *        ㅁ|ㅁ   ㅁㅁ             ㅁㅁ
 *
* */
public class Main {

    static int[] result = new int[100];
    public static void main(String[] args) {

    }

    public static int dp(int x) {
        if (x == 1) {
            return 1;
        }
        if (x == 2) {
            return 3;
        }
        if (result[x] != 0) {
            return result[x];
        }
        return result[x] = dp(x - 1) + 2 * dp(x - 2); // 그래서 여기에 *2
    }
}


```
