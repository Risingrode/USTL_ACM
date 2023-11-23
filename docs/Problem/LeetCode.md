

# 力扣

> 题目来自于`剑指offer`
> 目的是为了总结leetcode上面自己不会的题目

# 第一题[原题](https://leetcode.cn/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/?envType=study-plan-v2&envId=coding-interviews)

```c++
class Solution {
public:
    int add(int a, int b) {
        int ans=0;
        while(b){
            ans=a^b;
            // 注意优先级
            b=((a&b)<<1);
            a=ans;
        }
        return ans;
    }
};
```
解析：
我们来看看代码是如何实现这个二进制加法的过程的：
1. 首先，定义一个整数变量 `ans` 并初始化为0，用来存储计算结果。
2. 使用 `while` 循环进行加法计算，循环的结束条件是 `b` 不为0。这是因为当 `b` 为0时，说明没有进位了，加法运算已经结束，此时计算结果即为 `ans`
3. 在循环体内部，我们进行以下操作：
   - 通过异或运算 `a ^ b` 计算当前位的无进位和，并将结果存储在 `ans` 中。这是因为异或运算可以得到不考虑进位的加法结果。
   - 然后，通过位运算 `(a & b) << 1` 计算当前位的进位，并将结果存储在 `b` 中。这里的 `<< 1` 表示将进位左移一位，这样它就能与下一位相加。通过 `a & b`，我们可以得到当前位上的进位信息。
4. 重复执行步骤3，直到进位 `b` 为0，循环结束。
5. 返回计算结果 `ans`，即两个整数的和。
下面是逐步解释代码中的例子 `a = 5` 和 `b = 3`：

思路：拿到无进制和，拿到进制和，无进制和与进制和进行无进制和操作，直到，进制和变为0.


# 第二题 [思维题](https://leetcode.cn/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/description/?envType=study-plan-v2&envId=coding-interviews)

`注意：连续的正整数`

> 输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

![](/post/leetcode/2.jpg)


# 第三题 [约瑟夫环](https://leetcode.cn/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/solutions/178427/huan-ge-jiao-du-ju-li-jie-jue-yue-se-fu-huan-by-as/?envType=study-plan-v2&envId=coding-interviews)


```c++
class Solution {
public:
    int lastRemaining(int n, int m) {
       //只关心最终活着那个人的序号变化
       int pos=0;
       for(int i=2;i<=n;i++)
       // 这个是逆推，最后剩余2个人的时候，推导最后剩余3个人的时候。
       // 一直推到，最后剩余n个人。
            pos=(pos+m)%i;
        return pos;
    }
};
```


# 第四题 [查找数字](https://leetcode.cn/problems/ba-zi-fu-chuan-zhuan-huan-cheng-zheng-shu-lcof/description/?envType=study-plan-v2&envId=coding-interviews)

> 写一个函数 StrToInt，实现把字符串转换成整数这个功能。不能使用 atoi 或者其他类似的库函数。


```c++
class Solution {
public:
    int strToInt(string str) {
        bool sign = true;   //默认为正数
        //先舍弃开头可能存在的空格
        int i = 0;
        while(i < str.size() && str[i] == ' ') i++;
        //接着判断首个字符是否为正负号
        if(str[i] == '-') {
            sign = false; 
            i++;      
        }
        else if(str[i] == '+') i++; 

        if(str[i] < '0' || str[i] > '9') return 0; 
        int res = 0;  
        int num;
        int border = INT_MAX / 10; 
        while(i < str.size()){
            if(str[i] < '0' || str[i] > '9') break;
            if(res > border || res == border && str[i] > '7')
            return sign == true ? INT_MAX : INT_MIN;
            //开始对数字字符进行转换
            num = str[i] - '0';
            res = res * 10 + num;
            i++;
        }
        //最后结果根据符号添加正负号
        return sign == true ? res : -res;
    }
};
```

# 接雨水[原题](https://leetcode.cn/problems/trapping-rain-water/)

![](/post/leetcode/3.jpg)


[讲解视频链接](https://www.bilibili.com/video/BV1Qg411q7ia/?vd_source=5c0fbacddc9b27f70f605f6cbf43d269)

```c++
class Solution {
public:
    int trap(vector<int>& height) {
        int n=height.size();
        int l=0,r=n-1,ans=0;
        int pm=0,sm=0;
        while(l<r){
            pm=max(pm,height[l]);
            sm=max(sm,height[r]);
            if(pm<sm){
                ans+=(pm-height[l]);
                l++;
            }
            else{
                ans+=(sm-height[r]);
                r--;
            } 
        }
        return ans;
    }
};
```




# [最长不包含重复的子串](https://leetcode.cn/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/description/)


```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char,int>window;
        int l=0,r=0，res=0;
        while(r<s.size()){
            char c=s[r];
            r++;
            window[c]++;
            while(window[c]>1){// 记录区间[l,r]是否含有重复子串
                char d=s[l];
                l++;
                window[d]--;
            }
            res=max(res,r-l);
        }
        return res;
    }
};
```


# [矩阵中的路径](https://leetcode.cn/problems/ju-zhen-zhong-de-lu-jing-lcof/description/?envType=study-plan-v2&envId=coding-interviews)

> 给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true；否则，返回 false 。


```c++
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        int n=board.size(),m=board[0].size();
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(board[i][j]==word[0]){
                    if(dfs(board,word,i,j))
                        return true;
                }
            }
        }
        return false;
    }
private:
    bool dfs(vector<vector<char>>& board, string word,int i,int j){
        if(word.size()==0)return true;
        if(i<0||i>=board.size()||j<0||j>=board[0].size())return false;
        if(board[i][j]!=word[0])return false;
        char tem=board[i][j];
        board[i][j]='/';// 标记被找过了 这个是很巧妙的
        // string nword(word.begin() + 1, word.end());
        word=word.substr(1);// 截取函数，从下标1开始截取
        bool ans=dfs(board,word,i+1,j)||
                 dfs(board,word,i,j+1)||
                 dfs(board,word,i-1,j)||
                 dfs(board,word,i,j-1);
        // 回溯思想
        board[i][j]=tem;
        return ans;
    }
};

```



# 快速排序

> 关键在于边界问题，传入0,n, i=0-1,j=n+1,找一个基准x，下标是i+j>>1;
> 按照i < j 条件进行do while循环，找到左边大于x的，找到右边小于x的，进行swap;
> 递归  [l,j],[j+1,r]


```c++
// 数组是从0开始的。
void quick_sort(int q[], int l, int r)
{
    if (l >= r) return;
    // 这里的l-1和r+1 越界了，但是使用的是do while 语句，不会越界
    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while (i < j)
    {
        do i ++ ; while (q[i] < x);
        do j -- ; while (q[j] > x);
        if (i < j) swap(q[i], q[j]);
    }
    quick_sort(q, l, j), quick_sort(q, j + 1, r);
}

```

# [二叉搜索树与双向链表](https://leetcode.cn/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/description/?envType=study-plan-v2&envId=coding-interviews)

> 输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。

![](/post/leetcode/4.jpg)

```c++
class Solution {
public:
    // 前驱节点pre 
    Node* pre ,* head;
    void dfs(Node* cur){
        if(cur==nullptr)return ;
        dfs(cur->left);
        // 这个地方当前cur 是2，pre 是1 ，是cur左节点指向pre,
        // 需要修改成 pre 右节点指向cur,cur 左节点指向pre
        if(pre!=nullptr) pre->right=cur;
        else head=cur;// 表示正在访问链表头节点 记录一下，最后要用到
        cur->left=pre;
        pre=cur;// 更新一下前驱节点
        dfs(cur->right);
    }

    Node* treeToDoublyList(Node* root) {
        if(!root)return nullptr;
        dfs(root);
        head->left=pre;
        pre->right=head;
        return head;
    }
};
```



# [重建二叉树](https://leetcode.cn/problems/zhong-jian-er-cha-shu-lcof/description/?envType=study-plan-v2&envId=coding-interviews)

> 输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。
> 假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

```c++
class Solution {
public:
    TreeNode* buildTree(vector<int> preorder, vector<int> inorder) {
        int n=preorder.size();
        if(!n) return NULL;
        int rVal=preorder[0],rIndex=0;
        for(int i=0;i<n;i++)
            if(inorder[i]==rVal){
                rIndex=i;
                break;
            }
        TreeNode* root=new TreeNode(rVal);
        root->left = buildTree(vector<int>(preorder.begin() + 1, preorder.begin() + 1 + rIndex),vector<int>(inorder.begin(), inorder.begin() + rIndex));
        root->right = buildTree(vector<int>(preorder.begin() + 1 + rIndex, preorder.end()),vector<int>(inorder.begin() + rIndex + 1, inorder.end()));
        return root;
    }
};
```


# [最长不含重复子串](https://leetcode.cn/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/submissions/?envType=study-plan-v2&envId=coding-interviews)
```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char,int>window;
        int l=0,r=0,res=0;
        while(r<s.size()){
            char c=s[r];
            r++;
            window[c]++;
            while(window[c]>1){// 记录区间[l,r]是否含有重复子串
                char d=s[l];
                l++;
                window[d]--;
            }
            res=max(res,r-l);
        }
        return res;
    }
};
```


# [二叉搜索树的后续遍历](https://leetcode.cn/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/description/?envType=study-plan-v2&envId=coding-interviews)

> 熟练掌握二叉搜索树。

```c++
class Solution {
public:
    bool dfs(vector<int>&v,int l,int r){
        if(l>=r)return true;
        int mx=v[r],idx=l;
        while(v[idx]<mx)idx++;
        int m=idx;//右子树第一个点
        while(idx<r){
            // 如果m~r 区间出现比mx小的点，则不会是后续遍历
            if(v[idx]<mx)
                return false;
            idx++;
        }
        return dfs(v,l,m-1)&&dfs(v,m,r-1);
    }
    bool verifyPostorder(vector<int>& postorder) {
        return dfs(postorder,0,postorder.size()-1);
    }
};
```


# 归并排序


```c++
void merge_sort(int q[], int l, int r){
    //递归的终止情况
    if (l >= r) return;
    //第一步：分成子问题
    int mid = l + r >> 1;
    //第二步：递归处理子问题
    merge_sort(q, l, mid);
    merge_sort(q, mid + 1, r);
    //第三步：合并子问题
    int k = 0, i = l, j = mid + 1;
    while (i <= mid && j <= r)
        if (q[i] <= q[j]) tmp[k ++ ] = q[i ++ ];
        else tmp[k ++ ] = q[j ++ ];
    while (i <= mid) tmp[k ++ ] = q[i ++ ];
    while (j <= r) tmp[k ++ ] = q[j ++ ];
    //第四步：复制回原数组
    for (i = l, j = 0; i <= r; i ++, j ++ ) 
        q[i] = tmp[j];
}
```

[例题P51](https://leetcode.cn/problems/shu-zu-zhong-de-ni-xu-dui-lcof/description/?envType=study-plan-v2&envId=coding-interviews)：
> 在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。
```c++
class Solution {
public:
    int merge_sort(vector<int>& q,vector<int>& tmp, int l, int r){
        if (l >= r) return 0;
        int mid = (l + r) >> 1;
        int ans=merge_sort(q,tmp, l, mid)+merge_sort(q,tmp, mid + 1, r);
        int k = 0, i = l, j = mid + 1;
        while (i <= mid && j <= r)
            if (q[i] <= q[j]) tmp[k ++ ] = q[i ++ ],ans+=(j-mid-1);
            else tmp[k ++ ] = q[j ++ ];
        
        while (i <= mid) tmp[k ++ ] = q[i ++ ],ans+=(j-mid-1);
        while (j <= r) tmp[k ++ ] = q[j ++ ];
        for (i = l, j = 0; i <= r; i ++, j ++ ) 
            q[i] = tmp[j];
        return ans;
    }
    int reversePairs(vector<int>& nums) {
        int n=nums.size();
        vector<int>tmp(n);
        return merge_sort(nums,tmp,0,n-1);
    }
};
```

# KMP

> KMP算法的本质就是寻找子串的最长前后缀

```c++
#include<iostream>
#include<cstdio>
using namespace std;
const int N = 1e6 + 10;
int n, m, ne[N];
char p[N], s[N];
int main() {
    scanf("%d%s%d%s", &n, p + 1, &m, s + 1);
    for (int i = 2, j = 0; i <= n; ++i) {
        while (j && p[i] != p[j + 1]) j = ne[j];
        if (p[i] == p[j + 1]) j++;
        ne[i] = j;
    }
    for (int i = 1, j = 0; i <= m; ++i) {
        while (j && s[i] != p[j + 1]) j = ne[j];
        if (s[i] == p[j + 1]) j++;
        if (j == n) {
            printf("%d ", i - n);
            j = ne[j];
        }
    }
    return 0;
}

```

