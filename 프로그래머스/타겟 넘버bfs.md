```
class Solution {
    public static int answer = 0;
    public static int[] nums;
    public int solution(int[] numbers, int target) {
        nums = numbers.clone();

        bfs(1,numbers[0],0,target);
        bfs(1,-numbers[0],0,target);
        return answer;
    }
    private void bfs(int depth, int current,int sum,int target) {
        int total = sum + current;

        if (depth == nums.length) {
            if (total == target) {
                answer++;
            }
            return;
        }


        bfs(depth + 1, nums[depth],total,target);
        bfs(depth + 1, -nums[depth],total,target);
    }
}
```
