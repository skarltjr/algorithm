```bash
package algo;


import java.lang.reflect.Array;

/**
 * 1 10 5 8 7 6 4 3 2 9
 * 옆에 값과 비교하여 작은 값을 앞으로 보내면?
 * 버블 정렬 - 굉장히 비효율적
 * O(n^2)
 * */
public class Main {
    public static void main(String[] args) {
        int[] ints = {1, 10, 5, 8, 7, 6, 4, 3, 2, 9};


        for (int i = 0; i < 10; i++) {
            for (int j = i; j < 10; j++) {
                if (ints[i] > ints[j]) {
                    int temp = ints[i];
                    ints[i] = ints[j];
                    ints[j] = temp;
                }
            }
        }
        for (int anInt : ints) {
            System.out.println(anInt);
        }

    }
}
```
