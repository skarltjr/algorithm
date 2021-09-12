```
package algo;


/**
 * 에라토스테네스의 체 - 소수 판별
 * 1과 자기자신만을 약수로 갖는 수를 찾아라
 * 생각 -
 * ex) 8이 소수인지 판별할때 사실 (int)8의 제곱근까지만 검사해보면된다
 * 왜냐하면 8 = 2*4 =2*2*2 / 6 = 2*3  / ==> 결국 3,4까지 확인할 필요도 없이 2로 나눴을 때 나머지가 생기느냐 여부로 확인하면된다
 * 예를들어 27이라면 27의 (int)sqrt(27) = 5
 * 27 = 3*9 = 3*3*3 3의 배수까지 거칠필요없이 3으로만 확인할 수 있으면 된다.
 *
 *
 * (int)sqrt(8) = 2이고  2부터 2까지 = 2
 * 2로 8을 나눴을 때 나머지가 0이 아니라면 소수
 *
 * 만약 11이라면 (int)sqrt(11) = 3
 * 2~3
 * 11%2 == 0
 * 11%3 == 0
 * 은 모두 거짓이니 소수
 *
 * ---------------------
 *
 * 그런데 하나의 수가 소수인지 판별이 아니라
 * 대량의 소수를 한 번에 판별하고자 할 때 = 에라토스테네스의 체
 * 1. 1~25까지 있다고 했을 때 배열을 만든다.
 * 2. 2부터 시작하는데 자기 자신은 지우지 않고 2의 배수를 모두 지운다
 * 3. 3도 동일
 * --> 결국 이 배수를 모두 지운다는 것을 통해 소수만 남긴다
 * */
public class Main {

    // 하나의 수가 소수인지 판별
    static boolean isPrimeNum(int x) {
        int end = (int) Math.sqrt(x);
        System.out.println(end);
        for (int i = 2; i <= end; i++) {
            if (x % i == 0) {
                return false;
            }
        }
        return true;
    }

    static int[] array = new int[26];
    // 에라토스테네스의 체
    static void primeNums() {
        for (int i = 1; i <= 25; i++) {
            array[i] = i;
        }

        for (int i = 2; i <= 25; i++) {
            if (array[i] == 0) { // 0은 지워졌다는 의미
                continue;
            }

            for (int j = i + i; j <= 25; j = j + i) {
                // 만약 i=2라면 2 자기자신 빼고 2의 배수를 다 지우는 것
                array[j] = 0;
            }
        }

        for (int i = 1; i <= 25; i++) {
            if (array[i] != 0) {
                System.out.println(array[i]);
            }
        }
    }
    public static void main(String[] args) {
        //System.out.println(isPrimeNum(7));
        primeNums();

    }


}


```
