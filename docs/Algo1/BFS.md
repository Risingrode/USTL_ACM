# BFS(宽度优先遍历)

## 一、前置知识点：

数据结构：队列queue

## 二、BFS常用于解决的问题：

1.求最短路/最优计划(要求每次的代价相同)

2.常用于统计连通块等问题(flood fill)算法

## 三、代码模板

```c++
queue<int> q;

st[1] = true; // 表示1号点已经被遍历过

q.push(1);

while (!q.empty()) {
    int t = q.front();
    q.pop();

    for (int i = h[t]; i != -1; i = ne[i]) {
        int j = e[i];
        if (!st[j]) {
            st[j] = true; // 表示点j已经被遍历过
            q.push(j);
        }
    }
}
```

## 四、相关讲解

AcWing算法基础课：第三讲-搜索与图论

## 五、相关题目

### 求最短路径/最优计划

1. [B3625 迷宫寻路 - 洛谷 | 计算机科学教育新生态 ](https://www.luogu.com.cn/problem/B3625)
2. [迷宫 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/2222/learning/?page=1&first_category_id=1&sort=students_count&tags=BFS)
3. [844. 走迷宫 - AcWing题库](https://www.acwing.com/problem/content/846/) （模板题）
4. [845. 八数码 - AcWing题库](https://www.acwing.com/problem/content/847/)

### flood fill 连通块统计相关

1. [USTL OJ | 统计个数](http://39.106.70.121/problem/521E)
2. [PTA | 程序设计类实验辅助教学平台 (pintia.cn)](https://pintia.cn/problem-sets/994805046380707840/exam/problems/1649748772841508875?type=7&page=1)
3. [1233. 全球变暖 - AcWing题库](https://www.acwing.com/problem/content/1235/)