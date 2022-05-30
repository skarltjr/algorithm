```
package algo;


import java.util.*;

class Solution {
    static int count = 0;
    public int solution(int n, int k) {
        // k 진수로 변환
        String target = convertK(n, k);
        String temp = "";
        for (int i = 0; i < target.length(); i++) {
            for (int j = i+1; j <= target.length(); j++) {
                temp = target.substring(i, j);
                //check Prime
                if (checkIsPrime(temp)) {
                    //0P0처럼 소수 양쪽에 0이 있는 경우
                    if (i - 1 >= 0 && j < target.length() && target.charAt(i - 1) == '0' && target.charAt(j) == '0') {
                        count++;
                        continue;
                    }
                    //P0처럼 소수 오른쪽에만 0이 있고 왼쪽에는 아무것도 없는 경우
                    if (i == 0 && j < target.length()  && target.charAt(j) == '0') {
                        count++;
                        continue;
                    }
                    //0P처럼 소수 왼쪽에만 0이 있고 오른쪽에는 아무것도 없는 경우
                    if (j == target.length() && i > 0 && target.charAt(i - 1) == '0') {
                        count++;
                        continue;
                    }
                    //P처럼 소수 양쪽에 아무것도 없는 경우
                    if (i == 0 && j == target.length()) {
                        count++;
                        continue;
                    }
                }
            }
        }

        return count;
    }

    private boolean checkIsPrime(String temp) {
        if (temp.contains("0")) {
            return false;
        }
        Long targetNum = Long.parseLong(temp);
        if (targetNum == 1) {
            return false;
        }
        if (targetNum == 2) {
            return true;
        }

        for (int i = 2; i <= Math.sqrt(targetNum); i++) {
            if (targetNum % i == 0) {
                return false;
            }
        }
        return true;
    }

    private String convertK(int n, int k) {
        StringBuilder target = new StringBuilder();
        while (n >= k) {
            int next = n % k;
            target.append(next);
            n /= k;
        }
        target.append(n);
        return target.reverse().toString();
    }
}
```
