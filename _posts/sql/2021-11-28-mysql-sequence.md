---
title: "[mysql] mysql에서 시퀀스 생성하기"
date: 2021-11-28 16:40:28 +0900
categories: sql
tags: 
  - mysql
---



### mysql에서는 시퀀스 기능이 미지원

예전에 만들었던 프로젝트를 리팩토링하는 과정에서, 기존 DB를 oracle에서 mysql로 옮기고자 시도하였다.  
이유는 단순히 회사에서 mariadb를 사용하기 때문에...근데 mariadb보단 mysql도 한번 써보고 싶었다.

근데 생각치 못한 문제에 봉착했다.  
바로 mysql에서는 시퀀스 기능을 지원하지 않는 것이다.

그래서 다음 글을 참조하면서 sequence 기능을 구현해보고자 한다.



### References

- https://proudin.tistory.com/28