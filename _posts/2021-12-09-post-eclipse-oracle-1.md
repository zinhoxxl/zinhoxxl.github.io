---
layout: post
title: M1 으로 oracle & eclipse 연동하기 (1)
subtitle: M1 생존기
gh-repo: daattali/beautiful-jekyll
gh-badge: [zinhoxxl]
tags: [M1, Macbook, ios]
comments: true
---

**M1맥북으로 오라클 과 이클립스를 연동하기 그첫번째, 오라클 클라우드 지갑 다운받기**

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/43d68fbc-244b-47e8-b7c6-d27c649a7276/Oracle_Cloud_4f8.jpeg)

# ❶오라클클라우드 전자지갑으로 DB 생성>> #

<BR>

## 왜 이글을 적고있는가... ##


내가 기존에 사용하던것은 인텔맥북19년형 이었다.. 그러나 어느날 점심을 먹고오니 로직보드가 벽돌이되는 바람에 갈아타게 되어 현재 M1 에어로 코딩을 하고있다.
비전공자인 내가 택한 국비지원학원에서는 이클립스와 오라클을 사용중인데
웬걸.... 다른동기들이 따라가는 동안 나는 로컬호스트로 접근할수없어 오라클데이터베이스를 사용못하는 참사가 벌어졌다 ㅎㅎ
혼자알아보던중 강사님께서 다른 동기들을 도와주시는 것을 보고 도움을 요청했으나... 강사님께서는 슬프게도 맥북으로 한영 전환 하는 방법도 모르시는 분이었다,,
하지만 수업을 따라가야 했던 나는 포기할수없었고 끝내 방법을 찾아내었다..!

<BR>

## 맥북으로 오라클 사용은 불가능한 일일까? ##

아니다, 사용할수있다 
하지만 나는 sys계정을 통한 터미널창으로는 접근이 불가능하였다..

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/0fe26442-7623-41b9-8404-87ce521d805f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.49.25.png)


~~~
ORA-12547: TNS:lost contact 라는 에러메세지가 떴는데
커널파라미터나, 오라클 권한의 설정문제 일것 같다..
현재 수업후 틈틈히 알아보는 중이니 해결한다면 따로 글을 올리겠다.
~~~
<BR>




## 된다면 어떻게?? ##

나는 Oracle Cloud 전자지갑 을 활용해서 문제를 해결했다.<br>
<a href="https://cloud.oracle.com">https://cloud.oracle.com</a><br>
위의 링크를 타고 들어가면 오라클 클라우드 시작화면으로 가게된다

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/e0cdbe57-9969-4ae4-a17c-204d6c5476d2/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.17.04.png)

{: .box-note}
**ATP 데이터베이스 생성 을 선택하자!** 
<BR>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/157d1d59-55c1-497a-a0fe-da6fe010020b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.25.51.png)

여기서 데이터베이스이름을 잘 기억하자.
만약 이름을 oracle로 정했다면 tnsnames 접속명은 oracle이 될것이다.

<BR>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/a7f6c9da-1d92-46a6-80d6-0672ecc0ad42/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.31.18.png)


### 중요한건 데이터베이스 구성이다!

{: .box-warning}
**항상무료를 선택해야 혹시모를 과금폭탄을 피할수 있다..<br>
학습용으로 오라클을 하려는 것이기 때문에, 무료로 오라클이 제공해주는 저장공간은 국비지원학원 수업내용만 따라간다면 절대절대 부족할 일이 없다!** 

<BR>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/8e6259fe-84f1-4be0-8cd4-d678128d910a/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.38.50.png)

**관리자는 ADMIN**으로 되어있고 이것은 변경 불가 하다 ..<br>
그말인 즉슨 최고 통수권자는 동기들처럼 sys같은게 아닌 admin이니,<br>
sql developer 에서 사용시 잊지말기 바란다..

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/4aa6cf48-4f21-4953-9c3e-3b9e4790d965/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.45.42.png)

이제 다왔다... 라이센스 유형을 선택후 자율운영 데이터 베이스를 만들면 끝이다!!

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/b7206a40-7a74-4c34-be23-00b7b35ccab3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.55.43.png)

**생성이 잘된것을 확인 할 수 있다!**<br>
여기서 표시이름의 링크를 타고 들어가게되면,
<br>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/ff13d6a6-7ed9-4bdd-9aac-92cee8d4665e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.00.24.png)
![Crepe](https://media.vlpt.us/images/zinhoxxl/post/82c84789-3581-4dc3-82ca-80b846219d9f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.02.04.png)

<br>


### 이렇게 전자 지갑을 zip파일로 다운을 받는다! ###

<br>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/31ab3e5a-a79b-4805-801e-fea7a2c60fac/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.06.09.png)

지정하고 싶은 경로에 지갑을 압축해제하면 구성파일 중 tnsnames.ora 가있다.

```javascript
데이터베이스이름_high = (description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-seoul-1.oraclecloud.com))(connect_data=(service_name=g6e308e91853fd3_데이터베이스이름_high.adb.oraclecloud.com))(security=(ssl_server_cert_dn="CN=adb.ap-seoul-1.oraclecloud.com, OU=Oracle ADB SEOUL, O=Oracle Corporation, L=Redwood City, ST=California, C=US")))

데이터베이스이름_low = (description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-seoul-1.oraclecloud.com))(connect_data=(service_name=g6e308e91853fd3_데이터베이스이름_low.adb.oraclecloud.com))(security=(ssl_server_cert_dn="CN=adb.ap-seoul-1.oraclecloud.com, OU=Oracle ADB SEOUL, O=Oracle Corporation, L=Redwood City, ST=California, C=US")))

데이터베이스이름_medium = (description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-seoul-1.oraclecloud.com))(connect_data=(service_name=g6e308e91853fd3_데이터베이스이름_medium.adb.oraclecloud.com))(security=(ssl_server_cert_dn="CN=adb.ap-seoul-1.oraclecloud.com, OU=Oracle ADB SEOUL, O=Oracle Corporation, L=Redwood City, ST=California, C=US")))

데이터베이스이름_tp = (description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-seoul-1.oraclecloud.com))(connect_data=(service_name=g6e308e91853fd3_데이터베이스이름_tp.adb.oraclecloud.com))(security=(ssl_server_cert_dn="CN=adb.ap-seoul-1.oraclecloud.com, OU=Oracle ADB SEOUL, O=Oracle Corporation, L=Redwood City, ST=California, C=US")))

데이터베이스이름_tpurgent = (description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-seoul-1.oraclecloud.com))(connect_data=(service_name=g6e308e91853fd3_데이터베이스이름_tpurgent.adb.oraclecloud.com))(security=(ssl_server_cert_dn="CN=adb.ap-seoul-1.oraclecloud.com, OU=Oracle ADB SEOUL, O=Oracle Corporation, L=Redwood City, ST=California, C=US")))
```

이런 내용인데 tns 접속자를 확인할수 있다.<br>
tns alias 정보, 접속 프로토콜, 접속 주소 등이 나와있는데,<br>
잘보면 high, low, medium, tp, tpurgent 등으로 나누어져있다.<br>
그중 주된것의 특징은 이러하다.

{: .box-note}
**high :** 가장 성능이 좋고, 가장 응답속도가 빠르지만 동시실행가능한 sql문은 3개로 제한 적이다.


{: .box-warning}
**medium :** 동시실행 가능한 sql문이 high 보다는 많지만 동시실행이 가능한것이 많은 만큼 그 성능자체는 비교적 낮은 수준이다.


{: .box-error}
**low :** 동시실행 가능한 sql문이 가~장 많지만 제~일 구리다 처다보지 말자.

<Br>


<Br>

### 이렇게 오라클 클라우드로 전자지갑을 다운받는 방법을 기록했다! ###

<Br>

## 다음은 sql developer에서 다운받은 전자지갑을<br> 써먹어보자. ## 
........🛠🛠