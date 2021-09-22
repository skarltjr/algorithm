#### 매 순간 최적의 선택을 하자

1. https://www.acmicpc.net/problem/5585
- 거스름돈

```

import java.util.Scanner;

public class Main {


    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = 1000 - scanner.nextInt();
        int count = 0;
        // 500 , 100 ,50 ,10 ,5 ,1

        count += n / 500;
        n = n % 500;

        count += n / 100;
        n = n % 100;

        count += n / 50;
        n = n % 50;

        count += n / 10;
        n = n % 10;

        count += n / 5;
        n = n % 5;

        count += n / 1;
        n = n % 1;

        System.out.println(count);

    }
}

```


2. https://www.acmicpc.net/problem/11047

```

import java.util.Scanner;

public class Main {


    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int N = in.nextInt(); // 종류
        int K = in.nextInt(); // 만들고자 하는 합
        int[] val = new int[N];
        int count = 0;

        for (int i = 0; i < N; i++) {
            val[i] = in.nextInt();
        }

        for (int i = N - 1; i >= 0; i--) {
            count += K / val[i];
            K = K % val[i];
        }
        System.out.println(count);

    }
}

```

3. https://www.acmicpc.net/problem/1946
```
package algo;


import java.util.*;
/** 핵심 아이디어 :
 * 생각해보자 - 지금 서류 순으로 정렬을 했다
 * 그럼 서류 1등을 뺀 나머지애들은 서류 1등보다 다 서류가 낮다
 * 그럼 적어도 서류 1등보다 면접 점수가 높아야지만 무조건 통과 ★
 */

public class Main {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int number = in.nextInt();
        for (int i = 0; i < number; i++) {
            PriorityQueue<Volunteer> q = new PriorityQueue<>();

            int count = in.nextInt();
            for (int j = 0; j < count; j++) {
                int a = in.nextInt(); // 서류 등수
                int b = in.nextInt(); // 면접 등수
                q.add(new Volunteer(a, b));
            }



            Volunteer current = q.poll(); // 서류 1등
            int min = current.interview;

            int result = 1; // 서류 1등은 이미 합격
            for (int k = 1; k < count; k++) {
                Volunteer next = q.poll();
                if (min > next.interview) {
                    result++;
                    min = next.interview;
                }
            }

            System.out.println(result);
        }

    }
}

class Volunteer implements Comparable<Volunteer>{
    int docu; // 등수라는걸 잊지말자 낮을수록 좋은 것
    int interview;

    public Volunteer(int docu, int interview) {
        this.docu = docu;
        this.interview = interview;
    }

    @Override
    public int compareTo(Volunteer o) {
        if (o.docu == this.docu) {
            return o.interview > this.interview ? -1 : 1;
        } else {
            return o.docu > this.docu ? -1 : 1; // 양수일 때 자리변경
        }
    }
}
```
