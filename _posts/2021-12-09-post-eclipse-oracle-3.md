---
layout: post
title: M1 으로 oracle & eclipse 연동하기 (3)
subtitle: M1 생존기
gh-repo: daattali/beautiful-jekyll
gh-badge: [zinhoxxl]
tags: [M1, Macbook, ios]
comments: true
---

**이클립스에서 오라클DB 연동하기 그마지막!**

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/2e811348-f1d0-4538-9ad8-a63bf40f263e/eclipse-%E1%84%83%E1%85%A1%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%85%E1%85%A9%E1%84%83%E1%85%B3-%E1%84%8B%E1%85%B5%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B8%E1%84%89%E1%85%B3-%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5.png)

<p></p>

# ❸ eclipse 와 oracleDB 연동!>> #

<BR>

전자지갑으로 sql developer 에서 사용자를 생성하였다.<br>
이젠 학원에서 사용하는 eclipse 에서 oracleDB를 연동 해보겠다.

이클립스와 오라클을 연동한다 는 것은<br>
<p></p>
### 자바(JAVA)를 이용, 오라클에 생성한 테이블등에 접근하여 정보를 가져온다는 것을 의미한다. ###
연동을 위해서는 반드시 자바와 오라클DB의 연동을 위하여 ojdbc 라이브러리를 가져오는것이 필요한데<br> 
이 ojdbc 버전을 어떤것을 사용할지가 굉장히 큰문제였고,<br>
그로인해 매우 삽질과 고생을 하였다......💀<br>
(사전에 나는 수업으로는 jdk 버전을 8 을 사용한다는 점을 고지한다.)<br>
<br>
<br>
ojdbc 라이브러리는 오라클 홈페이지에서 제공하고있다<br>
<a href="https://www.oracle.com/database/technologies/jdbc-ucp-122-downloads.html">ojdbc 다운받기!!!!</a>  여기로 가면 다른버전,,다른 어떤것도 쳐다보지 말고
<p></p>

~~~
ojdbc 8-full.tar.gz
~~~

<p></p>

이걸 다운받도록 한다!!!!!!!!

<p></p>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/34a5e683-170a-4986-8b28-bff9eb829581/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.03.09.png)

<p></p>

다운받았다면 작업중인 workspace 폴더에 압축을 풀어준다<br>
그리고<br>
이클립스에 프로젝트를 생성하고 우클릭을하여 Build Path -> configure Build Path <br>
로 들어간다

<BR>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/06d49f25-6c3d-410b-9e57-ced14dfbd296/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.07.50.png)

<p></p>

Add External JARs... 를 클릭한다

<p></p>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/003d7d0a-8a0f-4cc2-b2da-3ea4a8a62de2/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.10.47.png)

<p></p>

ojdbc를 압축해제한 곳을 경로로 잡아서 ojdbc8.jar를 선택한다

<p></p>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/3fbcd5fb-39b7-425c-ba24-d19f1d5b5c57/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.13.14.png)

<p></p>

*정상적으로 ojdbc가 선택이되었다면 Apply and Close 를 눌러서 Build Path를 마친다!!!⚡️*

<BR>

그렇다면 이제 설정한 ojdbc 가 정상적으로 작동이 되는지 확인해보겠다<br>
자바Class를 하나만들어서 다음 코드를 입력한다.

~~~
import java.sql.Connection;
import java.sql.DriverManager;

/* 오라클 접속 테스트 */
public class ConnectTest_01 {
	public static void main(String[] args) {
       String url ="jdbc:oracle:thin:@데이터베이스이름_high?TNS_ADMIN=/전자지갑파일 경로/Wallet_데이터베이스이름";
       String userid="사용자 이름";
       String pwd ="비밀번호";
       
     
       //드라이버 로딩 
       try {
    	    //oracle DB연결 드라이버 로딩
    	    Class.forName("oracle.jdbc.OracleDriver");//
    	    System.out.println("드라이버 로딩 성공");
       }catch(Exception e) {
    	    e.printStackTrace();
       }
       
       //DBMS와 연결
       try {
    	       System.out.println("데이터베이스 연결 준비......");
    	       Connection con =DriverManager.getConnection(url, userid, pwd);
    	       if(con!=null) {
    	    	   System.out.println("데이터베이스 연결 성공...");
    	       }
       }catch(Exception e) {
    	   e.printStackTrace();
       }
	}
}
~~~

<p></p>
**여기서 중요한 것 몇개를 짚겠다! .. 내가 localhost로 오라클접근이 가능했다면**

<p></p>

~~~
String url ="jdbc:oracle:thin:@localhost:1521:xe";
~~~

이런식으로 했겠지만 우리는 전자 지갑을 사용했기에 좀 특별하다.<br>
만약내가 데이터베이스이름이 oracle이고 다운받은 전자지갑이 Wallet_oracle 이라면

<p></p>

~~~
String url ="jdbc:oracle:thin:@oracle_high?TNS_ADMIN=/전자지갑파일 경로/Wallet_oracle";
~~~

<p></p>

이런식으로 하면 된다. 전자지갑 파일 경로는 전자지갑 압축해제 한 바로 그경로이다.

<BR>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/f56a5cd8-aec2-4c55-a974-78d595351181/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.26.13.png)

<p></p>

이상태에서 option + command + c 를 눌러 파일경로를 복사하고
위의 전자지갑파일경로 에 붙여넣기한다.

<p>그리고 코드를 실행하면</p>

<BR>

<BR>

<BR>

### BoooYa⚡ ###

<p></p>

![Crepe](https://media.vlpt.us/images/zinhoxxl/post/d033cc59-f8f3-445f-8b98-270a4daadcf8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-08%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.29.32.png)

<p>콘솔 창에 데이터베이스 연결 성공이 잘 나온것을 확인할 수있다..</p>

성공!!!!!!!!<br>
👏🏼👏🏼👏🏼👏🏼👏🏼👏🏼👏🏼👏🏼<br>

<br>

이클립스에서 오라클DB를 연동하는 방법만 말하기때문에 이번글은 여기서 끝내겠다.<br>

<br>

<br>

## 마무리하며 .... ##
<br>
적어놓고보니 정말 아무것도 아니지만..<br>
백지상태에 M1에 관한 정보도 전무하고, 강사님의 도움도 받을 수 없던 나에게는<br>
수업을 잘못따라가는 것이 무척 부담이었다.<br>
구글에는 m1에서 오라클 을 시도한다니 비방하는 글로만 가득했지만💀<br>
누군가 어찌어찌 해낸글을 보았다.<br>
그건 분명 나에게 확신을 가져다줬다.<br>
m1은 문제가 아니다 , 안되는 건 내가 설정을 잘못했기 때문이다.<br>
라는 확신<br>
<br>
그렇기에 포기는 생각도 하지 않았다.<br>
이 고비를 넘기면 대단한 성취감이 날기다리고 있을것 같았고<br>
내가 해낼 수 있을 거라 믿었다<br>
매우 많은 시행착오가 있었다.... 무지속의 무지로 인해서 나는 모든 가능성을 열어두고<br>
경우의 수를 줄여가는 방법을 택했다<br>
주말을 반납하고 4일 을 몰두한 무지막지한 노가다였다<br>
직감적으로 너무 멀리 갔다는 느낌이 들어 다시 오라클 홈페이지의 영자로 적은 해결 방법을 보기로 했다<br>
근데 ojdbc 버전이..<br>
성공했다는 사람의 것과 그 안내글에 나온 버전이 달랐고<br>
혹시나 하는 마음에 8버전으로 갈아끼워 보니<br>
해결이되었다..<br>
그 과정에서 다른것도 알아보며 공부하던것 그리고 인내의 시간, 나에대한 믿음<br>
그리고 마지막 해결됬을때의 카타르시스는 지금도 짜릿하다<br>
별것아니지만 이로 인해 나는 많은 공부가 되었던거 같다<br>
이후에도 난 홀로 계속해서 새로운 수업이진행될때마다 새로운 난관에 봉착했지만<br>
이 때의 경험으로 해결해나가는 것 같다.<br>
<br>

<br>

<br>






<br>
<br>

### 앞으로도 화이팅!!!! ###

<br>
<br>