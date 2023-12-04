# BFS(宽度优先遍历)

## 一、前置知识点：

1.数据结构：队列queue

## 二、BFS常用于解决的问题：

1.求最短路/最优计划(要求每次的代价相同)

2.常用于统计连通块等问题(flood fill)算法

## 三、代码模板

```cpp
queue<int> q;

st[1] = true; // 表示1号点已经被遍历过

q.push(1);

while (q.size()) {
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

BFS例子:

一群老鼠走迷宫，假设老鼠有无限多。

在每个路口，都派出部分老鼠探索所有没走过的路。

走某条路的老鼠，如果碰壁无法前行，就停下。

如果到达的路口已经有别的老鼠探索过了，也停下。

所有的道路都会走到，而且不会重复。

这就是BFS。

---



例题：hdu 1312题

一个长方形的房间，铺着方砖，每块砖是 # 或黑点。。

一个人站在黑砖上，可以按上、下、左、右方向移动到相邻的砖。

他不能在#上移动，他只能在黑砖上移动。

起点是@，要求：遍历所有黑点。

起始图如下:

<img src="https://cwrisingblog.oss-cn-beijing.aliyuncs.com/ustl_acm/20231204215334.png"/>

BFS遍历图如下:

![89717b134077949bf53913803ca9ff1](https://cwrisingblog.oss-cn-beijing.aliyuncs.com/ustl_acm/clip_image004.gif)

BFS基本思想：

从初始状态S开始，利用规则，生成所有可能的状态。构成树的下一层节点，检查是否出现目标状态G，若未出现，就对该层所有状态节点，分别顺序利用规则。生成再下一层的所有状态节点，对这一层的所有状态节点检查是否出现G，若未出现，继续按上面思想生成再下一层的所有状态节点，这样一层一层往下展开。直到出现目标状态为止。

BFS算法：queue队列数据结构

- 把起始节点S线放到queue表中
- 如果queue是空表，则失败退出，否则继续。
- 在queue表中取最前面的节点node移到CLOSED 表中。（出队）
- 扩展node节点。若没有后继（即叶节点），则转向（2）循环。
- 把node的所有后继节点放在queue表的末端。各后继结点指针指向node节点。（入队）
- 若后继节点中某一个是目标节点，则找到一个解，成功退出。否则转向（2）循环。

## 五、相关题目



- 求最短路径/最优计划

   1.1: [B3625 迷宫寻路 - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/B3625)

   1.2: [迷宫 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/2222/learning/?page=1&first_category_id=1&sort=students_count&tags=BFS)

   1.3: [844. 走迷宫 - AcWing题库](https://www.acwing.com/problem/content/846/) （模板题）

   1.4: [845. 八数码 - AcWing题库](https://www.acwing.com/problem/content/847/)

- flood fill 连通块统计相关

   2.1: [USTL OJ | 统计个数](http://39.106.70.121/problem/521E)

   2.2: [PTA | 程序设计类实验辅助教学平台 (pintia.cn)](https://pintia.cn/problem-sets/994805046380707840/exam/problems/1649748772841508875?type=7&page=1)

   2.3: [1233. 全球变暖 - AcWing题库](https://www.acwing.com/problem/content/1235/)