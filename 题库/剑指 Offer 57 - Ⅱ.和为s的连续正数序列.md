用滑动窗口来解决问题

sum为窗口内的值的和，l为窗口左边界

当sum大于target时，左边界右移

当sum==target时，记录答案

## 复杂度

O(n)到O(n^2)之间  

### 执行用时

0ms

### 内存消耗

6.8MB 

```C++
class Solution {
public:
    vector<vector<int>> findContinuousSequence(int target) {
        int sum=1,l=1;
        vector<vector<int>>ans;
        for(int i=2;i<=(target+1)/2;i++){
            sum+=i;
            while(sum>target&&l<i){
                sum-=l;
                l++;
            }
            if(sum==target){
                vector<int>tmp;
                for(int j=l;j<=i;j++) tmp.push_back(j);
                ans.push_back(tmp);
            }
        }
        return ans;
    }
};
```

