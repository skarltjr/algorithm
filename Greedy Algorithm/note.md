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

