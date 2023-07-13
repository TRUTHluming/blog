---
title: 二分
date: 2023-05-21
tags: 算法
description: 学起来简单用起来难呐
categories: OI

---





# 二分   
具有单调性便一定可以二分，而不具有单调性也有部分是可以进行二分的。   
__但单调性并不与二分具有本源上的联系__
[模板题](https://www.acwing.com/problem/content/791/)
~~~c++   
#include <iostream>

using namespace std;

const int N = 100010;

int n, m;
int q[N];

int main()
{
    scanf("%d%d",&n,&m);
    for(int i = 0; i < n; i ++) scanf("%d",&q[i]);

    while(m --)
    {
        int x;
        scanf("%d",&x);
        int l = 0, r = n - 1;
        while(l < r)
        {
            int mid = l + r >> 1;
            if(q[mid] >= x) r = mid;
            else l = mid + 1;
        }

        if(q[l] != x) cout << "-1 -1" << endl;
        else
        {
            cout << l << " ";

            int l = 0, r = n - 1;
            while(l < r)
            {
                int mid = l + r +1 >> 1;
                if(q[mid] <= x) l = mid;
                else r = mid -1;
            }

            cout << l << endl;
        }
    }
    return 0;
}
~~~
将两种模板全都用在其中 ~~希望到时候不要自己看不懂~~          
然后浮点二分便还要简单得多了  
比如用二分求一个数的平方根
~~~c++     
#include <iostream>

using namespace std;

int main()
{
    double x;
    cin >> x;

    double l = 0, r = x;
    while(r - l > 1e-6)
    {
        double mid = (l + r) /2;
        if(mid * mid >= x) r = mid;
        else l = mid;
    }

    printf("%lf\n", l);

    return 0;
}
~~~

另外再写上个函数式模板

~~~c++
int bsearch_1(int l, int r)
{
    while (l < r)
    {
        int mid = l + r >> 1;
        if (check(mid)) r = mid;
        else l = mid + 1;
    }
    return l;
}
~~~



补一道题目

[愤怒的牛](https://www.acwing.com/problem/content/description/4179/)
初看题目，并不觉得和二分``有关``



但是再看，题目的要求是求出``最大``的``最小``距离值



也就是一个数 _n_ ，使所有牛之前的距离都大于 _n_,求n的最大值



既然这些都知道了，那先简单写一个check函数

~~~c++

bool check(int mid)
{
int num = 1;
int way = cow_house[1] + mid;
for(int i = 2; i <= n ; i ++)
{
    if(cow_house[i] < way) continue;
    num ++;
    way = cow_house[i] + mid;
}
return num >= m;

}

~~~



其后构造整个代码

~~~c++



#include <bits/stdc++.h>

using namespace std;

const  int maxn = 1e5 +10;


int cow_house[maxn], n , m;


bool check(int mid)
{
int num = 1;
int way = cow_house[1] + mid;
for(int i = 2; i <= n ; i ++)
{
    if(cow_house[i] < way) continue;
    num ++;
    way = cow_house[i] + mid;
}
return num >= m;

}

int insert(int l, int r)
{
    while(l <= r)
    {
        int mid = (l + r ) >> 1;
        if(check(mid)) l = mid+1;
        else r = mid-1;
    }

    return r;
}

int main()
{
    cin >> n >> m ;
    for(int i = 1; i <= n; i ++)
    {
        cin >> cow_house[i];
    }
    sort(cow_house + 1,cow_house+n+1);
    cout << insert(1, cow_house[n]);







    return 0;
}

~~~