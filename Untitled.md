
```js
var findTargetSumWays = function (nums, target) {
    const n = nums.length;
    //为了保证index为自然数，target+=sum(nums)
    target += nums.reduce((a, b) => a + b);
    //如果为奇数，根据加法原理必然不等，返回0
    if (target < 0 || target % 2 === 1) return 0;
    //所有正数的绝对值之和的方案数与target方案数量相同 所以只需要考虑选与不选即可
    target /= 2;
    const memo = new Array(n).fill().map(() => Array(target + 1));
    const dfs = function (i, c) {
        if (i < 0) return c === 0 ? 1 : 0;
        if (memo[i][c]) return memo[i][c];
        if (c < nums[i]) return memo[i][c] = dfs(i - 1, c);
        return memo[i][c] = dfs(i - 1, c) + dfs(i - 1, c - nums[i]);
    }
    return dfs(n - 1, target);
};
```