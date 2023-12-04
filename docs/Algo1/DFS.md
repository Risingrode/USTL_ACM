# DFS搜索

> DFS 为图论中的概念，在搜索算法中，该词常常指利用递归函数方便地实现暴力枚举的算法，与图论中的 DFS 算法有一定相似之处，但并不完全相同。DFS也就是通常同学们口中的暴力，写好DFS对蓝桥杯之类的OI赛制比赛有很大的帮助

## DFS搜索方式

e.x.:一只老鼠走迷宫

在每个路口，它都选择先走右边（当然，选择先走左边也可以），能走多远就走多远；

如果碰壁无法再继续往前走，就回退一步，这一次走左边，然后继续往下走。

重复前面步骤，能走遍所有的路，而且不会重复（这里规定回退不算重复走）。

这就是DFS。DFS就是一条路走到底，只有走到没有路可以走了才会返回，否则会一直搜索下去。

由于DFS较为灵活，没有什么固定的模版，本章只给大家列出一些经典的DFS题目供大家去练习。

DFS一般使用的情况为:题目要求输出所有的方案/情况等。当数据范围很小时可以考虑使用(一般小于100)

## 相关题目

## 全排列

- [P1706 全排列问题 - 洛谷 | 计算机科学教育新生态 (luogu.com.cn)](https://www.luogu.com.cn/problem/P1706)
- [14.飞机降落 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/3511/learning/?page=2&first_category_id=1&second_category_id=3&tags=2023)

## 树相关搜索（PTA 甲级有很多相关的题目）

- [846. 树的重心 - AcWing题库](https://www.acwing.com/problem/content/848/)
- [PTA | 程序设计类实验辅助教学平台 (pintia.cn)](https://pintia.cn/problem-sets/994805046380707840/exam/problems/1518582482059845632?type=7&page=1)

## 树的前序遍历、中序遍历、后序遍历等...

- [PTA | 程序设计类实验辅助教学平台 (pintia.cn)](https://pintia.cn/problem-sets/994805342720868352/exam/problems/994805367987355648?type=7&page=0)
- [92. 递归实现指数型枚举 - AcWing题库](https://www.acwing.com/problem/content/94/)

## 枚举方案等

- [P2089 烤鸡 - 洛谷 | 计算机科学教育新生态 (luogu.com.cn)](https://www.luogu.com.cn/problem/P2089)
- [Problem - E - Codeforces](https://codeforces.com/gym/104651/problem/E)









