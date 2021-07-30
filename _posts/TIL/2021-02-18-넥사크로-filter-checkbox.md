---
title: "[TIL] 210218_넥사크로 filter와 checkbox 선택 안되는 오류 해결"
date: 2021-02-18 19:02:28 +0900
categories: til
tags: nexacro
---


### Oracle 테이블 중간에 컬럼 넣기(12c 이상)

oracle 12c 이상부터는 컬럼의 invisible, visible 속성을 사용하면 된다.

원하는 위치까지 컬럼들을 invisible로 변경 후에, alter add 로 컬럼을 추가한 후, 다시 visible로 변경하면 테이블 가운데에 컬럼을 추가할 수 있다.

아쉽게도 나는 11c를 써서...작동되지 않았다. 다음에 업그레이드 되면 써보면 좋겠다.



### 넥사크로 - filter

- radio에 필터걸기
  - 주의 : bind dataset을 하지 않는다.
  - properties에 innerdataset을 추가한 후 code값과 data값을 넣어준다.
  - script에서 해당 radio에 onitemchanged 이벤트가 발생했을 때, e.postvalue를 받아서 (이게 code 값임) dataset에 filter를 걸어주면 된다.

```javascript
this.search_rdo_status = function(obj:nexacro.Radio,e:nexacro.ItemChangeEventInfo)
{
	if(e.postvalue == "A"){
		this.ds_sidebar.filter("");
	}else{
		this.ds_sidebar.filter("status == '" + e.postvalue + "'");
	}
};
```

- 키워드 검색을 통하여 관련 아이템 추출하기
  - combo의 type을 기존 dropdown에서 `filterlike`로 바꿔준다. `filterlike` 는 SQL 의 like문과 비슷한 역할을 하며, 포탈사이트에서 검색하듯이 밑에 목록을 띄워준다.



### 넥사크로 - checkbox 체크 안되는 오류

넥사크로 내에서 실행될 때는 체크가 잘 되는데, 서버에 배포하니까 체크박스가 안눌리는 문제가 발생하였다. 알고보니 넥사크로 dataset에서만 chk칼럼을 추가해 줄 뿐만 아니라, controller쪽에서도 chk에 값을 담아와야 했다. 

그래서 setChk 로 모두 0을 담아준 후, Grid에서도 checkboxfalsevalue 를 0, checkboxtruevalue를 1로 설정해주니 잘 동작하였다. 



### References

https://bit.ly/3jZEjyB - 넥사크로 설명서

https://flatsun.tistory.com/570 - 체크박스 체크가 되지 않을 때

https://gent.tistory.com/323 - 오라클 12c이상에서 테이블 중간에 컬럼 넣기
