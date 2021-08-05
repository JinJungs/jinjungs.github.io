---
title: "[python - 프로그래머스] 행렬의 곱셈"
date: 2021-03-25 18:58:28 +0900
tags: python
comments: true
published: true
categories: python
typora-copy-images-to: ..\..\img
---

```python
def solution(arr1, arr2):
    answer = []
    for i in arr1:
        x = []
        for k in range(len(arr2[0])):
            n = 0
            for j in enumerate(arr2):
                n += i[j[0]] * j[1][k]
            x.append(n)
        answer.append(x)
           
    return answer
```

