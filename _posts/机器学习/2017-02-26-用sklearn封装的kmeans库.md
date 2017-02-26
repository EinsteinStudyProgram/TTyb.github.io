---
layout: post
categories: [����ѧϰ]
title: ��sklearn��װ��kmeans��
date: 2017-02-26
author: TTyb
desc: "������Ҫ�����Ľ��о��࣬���Խ� `k-means` �㷨���ҷ�װ��һ���������õĿ�"
---

������Ҫ�����Ľ��о��࣬���Խ� `k-means` �㷨���ҷ�װ��һ���������õĿ⣬����ֱ�ӵ��õõ����ŵ� `kֵ` �� `���ĵ�`��

```
#!/usr/bin/python3.4
# -*- coding: utf-8 -*-

# k-means�㷨

import numpy as np
from sklearn.cluster import KMeans
from sklearn import metrics


def calckmean(array, karr):
    # array��һ����ά����
    # X = [[1, 2, 3, 4], [5, 6, 7, 8], [3, 4, 5, 6]]

    # k�Ǵ�ѡȡKֵ������
    # karr = [2, 3, 4, 5, 8,...]

    # ��ԭʼ�����������ɾ���

    x = np.array(array)

    # ������������ϵ��������
    score = []
    # ����������������������
    point = []

    for k in karr:
        kmeans_model = KMeans(n_clusters=k).fit(x)
        # title = 'K = %s, ����ϵ�� = %.03f' % (k, metrics.silhouette_score(X, kmeans_model.labels))
        # print(title)

        # ��ȡ���ĵ������
        counter_point = kmeans_model.cluster_centers_
        # print("k=" + str(k) + "ʱ�����ĵ�Ϊ" + "\n" + str(counter_point))

        # ��¼����
        # print(metrics.silhouette_score(x, kmeans_model.labels_))
        score.append("%.03f" % (metrics.silhouette_score(x, kmeans_model.labels_)))
        # ��¼��������
        point.append(counter_point)

    # ��������ϵ������kֵ������
    maxscore = max(score)

    for i in range(0, len(score)):
        if maxscore == score[i]:
            return karr[i], point[i]

```

���õ�ʱ��ֱ�ӿ��ԣ�

`from kmeans import *`

�������ݣ�

```
#!/usr/bin/python3.4
# -*- coding: utf-8 -*-

from kmeans import *

x1 = np.array([1, 2, 3, 1, 5, 6, 5])
x2 = np.array([1, 3, 2, 2, 8, 6, 7])

# a = [[1, 2, 3, 1, 5, 6, 5], [1, 3, 2, 2, 8, 6, 7], [3, 5, 9, 4, 7, 6, 1], [1, 5, 3, 4, 8, 6, 7], [5, 1, 2, 3, 6, 9, 4],[8, 4, 6, 2, 1, 6, 3]]
a = [[1, 1], [2, 3], [3, 2], [1, 2], [5, 8], [6, 6], [5, 7], [5, 6], [6, 7], [7, 1], [8, 2], [9, 1], [7, 1], [9, 3]]
karr = [2, 3, 4, 5, 8]
# print(np.array(a))
# print(list(zip(x1, x2)))

k, point = calckmean(a, karr)
print("��õĿ��Էֳ�" + str(k) + "���أ����ĵ�Ϊ" + "\n" + str(point))

```

![](http://images2015.cnblogs.com/blog/996148/201702/996148-20170226101819554-1837598147.png)

Դ�ļ��������ҵ�github���أ�

[TTyb](https://github.com/TTyb/kmeans)