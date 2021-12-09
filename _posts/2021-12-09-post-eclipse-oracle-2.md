---
layout: post
title: M1 으로 oracle & eclipse 연동하기 (2)
subtitle: M1 생존기
gh-repo: daattali/beautiful-jekyll
gh-badge: [zinhoxxl]
tags: [M1, Macbook, ios]
comments: true
---

**전자지갑으로 sql developer에 사용자를 생성해보자!**

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/7e1a47b5-96b7-44e5-add4-a3ac95b5de94/Oracle-SQL-Developer-logo.png)

지난글에 오라클 클라우드에서 전자지갑을 내려받았다.<br>
그렇다면 이제 수업에 사용하는 sql developer에 써먹을 시간이다.

혹시 아직 sql developer가 없다면..<br>
<a href="https://www.oracle.com/tools/downloads/sqldev-downloads.html">sqldev-downloads</a> 여기에가서 다운을 먼저받자!<br>
나는 homebrew로 다운받았지만 뭐로 해도 상관은 없다.

<BR>

<BR>


먼저 sql developer를 실행하면 좌측 상단에 녹색+(새접속) 가 있다.

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/e492a62d-313d-432f-ad86-c4b5ebf8834b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.00.47.png)

눌러서 **새로만들기/데이터베이스** 접속 선택 으로 간다.

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/0da3a90a-5812-4b83-9fb2-b3cd0f4c7bc8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.06.39.png)

~~~
Name :
좌측 슬라이드에 보여지는 이름으로 ~~접속 이런식으로 생성하였다
~~~

<p></p>

~~~
사용자 이름 / 비밀번호 :
DB에 접근할때 사용할 유저의 이름과 비번을 설정한다
~~~

<p></p>

~~~
접속유형 :
클라우드 전자 지갑을 선택, 구성파일은 전자지갑zip파일을 경로로 잡고, tns 접속자를 선택한다. 나는 high를 선택하였다.
~~~
<BR>

### 설정을 마치면 테스트를 눌러 "성공" 이 나오면 된다!! ###
<BR>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/c1d28fe3-b460-4b78-a4dc-366154cc7a11/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.18.35.png)
<p></p>
성공적으로 생성이 됬다면 좌측 슬라이드에 방금 Name에서 지어준 이름이 보인다.<br>
선택하면 접속 정보를 입력하면 되는데<br> 
이것 역시 방금 설정한 사용자이름 / 비번 을 입력하면 접속할 수 있다.
<p></p>
그럼
<br>
<br>
<br>
<br>
짜잔⭐️
<p></p>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/357d5f59-4cd9-45f4-86ab-84e7ca26f915/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.19.14.png)
<p></p>
 
### 성공적으로 접속한 것을 볼수있다!! ###

<BR>

이제 테이블도 생성하고 수업을 따라갈 수있게되었다!<br>
하지만 문제가 하나 더남았으니<br>
바로 오라클 db와 이클립스를 연동에 성공하는 것이다<br>
다음글에서는 마지막!! 이클립스에서 오라클db와 연동하는 방법을 적어보겠다..<br>
.....🛠🛠🛠
<br>
<br>
<br>
<br>