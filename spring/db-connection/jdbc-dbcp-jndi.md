# JDBC, DBCP, JNDI

**JDBC \(Java DataBase Connectivity\)**

데이터베이스풀 방식을 사용하지 않고 DB에서 정보를 가져올 때마다 매번 디비연결을 열고 닫는 방식

디비풀을 사용하지도 않고, 각 페이지에 데이터베이스 통신이 필요한 부분이 있으면 무조건 디비객체 생성, 커넥션 연결, 커넥션 종료 등 반복하기 때문에 효율이 매우 떨어진다.  


Java Application 안에서 SQL 문의 실행을 통해 데이터베이스와의 연동을 가능하게 해주는 Java API

JDBC의 가장 기본으로, 구현체는 스펙에 없고 interface만 존재하며

이를 구현한 드라이버가 DB Vendor 별로 있다.  
  
  
****

**DBCP\(Database Connection Pool\)**

기본적인 원리는 어플리케이션을 시작할 때 원하는 만큼 커넥션 객체를 만들어 놓고 pool에 넣어놓았다가 필요할 때마다 갖다 쓰고 pool에 반납하는 방식으로 운영한다.

다중 스레드를 스레드풀로 관리하는 것과 비슷한 방식.  


Apache Commons에서 만든 connection pool open source library.

일반적으로 DB 커넥션의 생성은 시간과 자원을 많이 사용한다.

미리 생성한 여러 개의 커넥션을 재사용하여 서버 부하 감소와 성능 증가의 효과를 가져올 수 있다.  
  
  
****

**JNDI \(Java Naming And Directory Interface\)**

DBCP처럼 어플리케이션 소스단에 설정하는 방식이 아닌 WAS단에 데이터베이스 커넥션 객체를 미리 네이밍 해두는 방식이다.

WAS단에 데이터베이스 풀을 미리 네이밍 해두면 이점이 있다.

대표적으로 DNS가 있다.  


디렉토리 서비스에서 제공하는 데이터 및 객체를 발견하고 참고\(lookup\)하기 위한 자바 API.

분산환경에서 DB 서버 커넥션의 위치를 네이밍을 통해 접근하도록 하는 J2EE 표준 기술.

DB 커넥션 정보를 WAS 단에서 관리. WAS의 context.xml 안에 정의한다.

JNDI 설정에서 커넥션 풀 설정을 따로 한다.  


JNDI를 사용하게 되면, DB의 Connection정보는 WAS에서 관리 하므로. 소스단에 노출되지 않는다. 

운영서버의 중요정보가 일반 개발자에게 노출되지 않음. 보안상의 이점이 있음.  
  
  
  
****

**https://all-record.tistory.com/104?category=733042**  


