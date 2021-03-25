---
title: "[프로그래머스]신규 아이디 추천"
date: 2021-03-25 18:58:28 -0400
tags: python
comments: true
published: true
categories: python
typora-copy-images-to: ..\..\img
---

### 신규 아이디 추천

```python
import re

def rm_period(arr):
  flag = True
  if len(arr)==0:
      flag = False
    
  while flag:
    if len(arr)==0:
      break
    if arr[0]=='.' or arr[-1]=='.':
      if arr[0]=='.':
        del arr[0]
      else:
        del arr[-1]
    if len(arr)==0:
      break
    if arr[0]!='.' and arr[-1]!='.':
      break

  return arr

def solution(new_id):
  #1단계
  tran_id = new_id.lower()
  #2단계
  tran_id = re.sub('[~!@#$%^&*\(\)=+\[\{\]\}:?,<>/]', '', tran_id)
  #3단계 - 2번이상 연속된 마침표 제거
  arr = list(map(str,tran_id))
  period = []
  for i in range(1,len(arr)):
    if arr[i-1]==arr[i] and arr[i]=='.':
      period.append(i-1)
  
  period = list(map(int,period))
  for j in range(len(period)-1,-1,-1):
    del arr[period[j]]

  #4단계 - 앞뒤 마침표 제거
  rm_period(arr)

  #5단계
  if len(arr)==0:
    arr.append('a')
  #6단계, 7단계
  if len(arr)>=16:
    del arr[15:]
  elif len(arr)<=2:
    while len(arr)<3:
      arr.append(arr[-1])

  # 한번 더 앞뒤 . 제거
  rm_period(arr)
  answer = ''.join(arr)
  return answer

print(solution("abcdefghijklmn.p"))
```



