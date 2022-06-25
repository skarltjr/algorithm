```

import java.util.*;

class Solution {
    public String solution(int n, int t, int m, int p) {
        StringBuilder sb = new StringBuilder();
        int count = 0;
        int index = 0;
        while (count < (m * t)) {
            String current = Integer.toString(index, n);
            sb.append(current);
            index++;
            count += current.length();
        }

        StringBuilder ans = new StringBuilder();
        int idx = 0;
        for (int i = 0; i < t; i++) {
            idx = (m * i) + p - 1;
            ans.append(sb.charAt(idx));
        }


        return ans.toString().toUpperCase(Locale.ROOT);
    }
}
```
