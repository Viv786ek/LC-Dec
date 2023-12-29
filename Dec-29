class Solution {
public:
    int minDifficulty(vector<int>& jobDifficulty, int d) {
        int len = jobDifficulty.size();
        if (len < d) {
            return -1;
        }
        int sum = accumulate(jobDifficulty.begin(), jobDifficulty.end(), 0);
        if (sum == 0) {
            return 0;
        }
        return helper(jobDifficulty, d, 0);
    }

private:
    int helper(vector<int>& jd, int daysLeft, int idx) {
        int len = jd.size();
        if (daysLeft == 1) {
            int num = 0;
            for (int i = idx; i < len; i++) {
                num = max(num, jd[i]);
            }
            return num;
        }

        int maxDifficulty = jd[idx];
        daysLeft--;
        int stop = len - idx - daysLeft + 1;

        int result = INT_MAX;
        for (int i = 1; i < stop; i++) {
            maxDifficulty = max(maxDifficulty, jd[idx + i - 1]);
            int other = helper(jd, daysLeft, idx + i);
            result = min(result, other + maxDifficulty);
        }
        return result;
    }
};
