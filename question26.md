# 第N个泰波那契数

泰波那契序列 Tn 定义如下： 

T0 = 0, T1 = 1, T2 = 1, 且在 n >= 0 的条件下 Tn+3 = Tn + Tn+1 + Tn+2

给你整数 `n`，请返回第 n 个泰波那契数 Tn 的值。

## 示例 1：
>### 输入：
>n = 4
>### 输出：
>4
>### 解释：
>T_3 = 0 + 1 + 1 = 2
>T_4 = 1 + 1 + 2 = 4

## 示例 2：
>### 输入：
>n = 25
>### 输出：
>1389537


## 代码：

### 递归法（超时）

    public class Solution {
        public int Tribonacci(int n) {
            if(n==0){
                return 0;
            }
            else if(n==2||n==1){
                return 1;
            }
            return Tribonacci(n-3)+Tribonacci(n-2)+Tribonacci(n-1);     
        }
    }

<u>递归方法计算三斐波那契数（Tribonacci 数）会导致指数级的时间复杂度，因为它会重复计算相同的子问题。为了提高效率，可以使用动态规划（Dynamic Programming）或记忆化递归（Memoization）来减少时间复杂度。</u>

### 正解
1.

    public class Solution {
        IDictionary<int, int> memo = new Dictionary<int, int>();

        public int Tribonacci(int n) {
            if (n == 0) {
                return 0;
            }
            if (n == 1 || n == 2) {
                return 1;
            }
            if (!memo.ContainsKey(n)) {
                memo.Add(n, Tribonacci(n - 1) + Tribonacci(n - 2) + Tribonacci(n - 3));
            }
            return memo[n];
        }
    }
2.

    public class Solution {
        public int Tribonacci(int n) => (int)((Math.Pow(33 * (99 - 17 * Math.Sqrt(33)), 1 / 3.0) + Math.Pow(33 * (99 + 17 * Math.Sqrt(33)), 1 / 3.0)) / 66.0 * Math.Pow((1 + Math.Pow(19 - 3 * Math.Sqrt(33), 1 / 3.0) + Math.Pow(19 + 3 * Math.Sqrt(33), 1 / 3.0)) / 3.0, n) + 1 / 2.0);
    }
3.

    public class Solution {
        public int Tribonacci(int n) {
            if (n == 0) return 0;
            if (n == 1 || n == 2) return 1;

            int a = 0, b = 1, c = 1;

            for (int i = 3; i <= n; i++) {
                int sum = a + b + c;
                a = b;
                b = c;
                c = sum;
            }

            return c;
        }
    }
