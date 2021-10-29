```
package algo;


/**
 *
 * 1. 한 번에 한 개의 알파벳만 바꿀 수 있습니다.
 * 2. words에 있는 단어로만 변환할 수 있습니다.
 *
 *
 * 이미 확인한거 또 확인하면 최단거리가 될 수 없다 + 사이클생길 수 있고
 *                                  hit
 *                          hot dot dog lot log cog
 *            dot dog lot log cog
 *
 *
 *      hit -> hot -> dot ->. ...
 *   쭉 들어가보고 맞으면 횟수비교 후 최소값이면 change answer
 *   쭉 들어가보고 아니면 한 걸음 뒤로 와서 다른애로 dfs들어가고
 */
class Solution {
    static int answer = 10000;

    public int solution(String begin, String target, String[] words) {
        boolean exist = false;
        for (int i = 0; i < words.length; i++) {
            if (words[i].equals(target)) {
                exist = true;
            }
        }
        if (exist == false) {   // 타겟이 words에 존재하는지 확인
            return 0;
        }

        boolean[] visited = new boolean[words.length]; // dfs마다 다른 visited배열을 가져야하니까 static으로 쓸 수 없었다
        dfs(begin,target,words,visited,0);

        if (answer == 10000) {
            return 0;
        }
        return answer;
    }

    private void dfs(String source, String target, String[] words, boolean[] visited,int turn) {
        if (source.equals(target)) {
            if (answer > turn) {
                answer = turn;
            }
        }

        for (int i = 0; i < words.length; i++) {
            if (!visited[i] && check(source,words[i])) {
                visited[i] = true;
                dfs(words[i],target,words,visited,turn+1);
            }
        }

    }
    private boolean check(String source,String target) {
        // 한 글자만 바꿔서 change할 수 있는지 check
        int changed = 0;
        for (int i = 0; i < source.length(); i++) {
            if (source.charAt(i) != target.charAt(i)) {
                changed++;
            }
        }

        if (changed == 1) {  // 실수 : 하나만 바뀌어야한다. 0개 바뀌는것도 false
            return true;
        }
        return false;
    }

}
```
