```bash
package algo;


import java.lang.reflect.Array;

/**
 * 1 10 5 8 7 6 4 3 2 9
 * 가장 작은 놈을 선택해서 앞으로 보내는
 * 선택 정렬
 * O(n^2)
 * */
public class Main {
    public static void main(String[] args) {
        int[] ints = {1, 10, 5, 8, 7, 6, 4, 3, 2, 9};
        int index = -1;
        for (int i = 0; i < 10; i++) {
            int min = 999;
            for (int j = i; j < 10; j++) {
                if (min > ints[j]) {
                    min = ints[j];
                    index = j;
                }
            }
            int temp = ints[i];
            ints[i] = min;
            ints[index] = temp;
        }
        for (int anInt : ints) {
            System.out.println(anInt);
        }

    }
}

```
