---
title: 二分
date: 2023-06-03
tags: 算法
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
将两种模板全都用在其中~~希望到时候不要自己看不懂~~          
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
