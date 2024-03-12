class Solution {
    private static long[][] mat = new long[3][3];
    private static long[][] res = new long[3][3];

    private static void mul(long[][] res, long[][] mat, long m) {
        long[][] res1 = new long[3][3];
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                for (int k = 0; k < 3; k++) {
                    res1[i][j] += (res[i][k] * mat[k][j]) % m;
                    res1[i][j] %= m;
                }
            }
        }

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                res[i][j] = res1[i][j];
    }

 
    private static void mat_exp(long n, long m) {
        while (n > 0) {
            if ((n & 1) == 1)
                mul(res, mat, m);
            mul(mat, mat, m);
            n /= 2;
        }
    }

   
    static long genFibNum(long a, long b, long c, long n, long m) {
        for (long[] row : res)
            Arrays.fill(row, 0);

        res[0][0] = res[1][1] = res[2][2] = 1;
        mat[0][0] = a;
        mat[0][1] = b;
        mat[0][2] = mat[1][0] = mat[2][2] = 1;
        mat[1][1] = mat[1][2] = mat[2][0] = mat[2][1] = 0;

        if (n <= 2)
            return 1 % m;
        else {
            mat_exp(n - 2, m);
            return (res[0][0] + res[0][1] + c * res[0][2]) % m;
        }
    }
}