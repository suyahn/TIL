#1. MySQL

##MySQL 특징

- sql에 기반을 둔 관계형 DBMS
- 무료
- 거의 모든 운영체제에서 사용 가능
- 처리속도가 상당히 빠르고 대용량 데이터 처리 용이
- 설치방법이 쉽고 초보자도 익히기 쉬움
- 보안성 우수

---------------------------

##데이터베이스 생성

    create database 데이터베이스명;

##존재하는 데이터베이스 목록보기

    show databases;

##테이블 목록 보기

    show tables;

##테이블 구조 보기

    desc 테이블명;

--------------------------

#2. DCL (Data Control Language)

##권한 부여

    grant 권한 on db명.table명 to user명 [identified by '암호'] [with grant option];

with grant option을 받은 user는 그 권한을 다른 user에게 줄 수 있게 된다.


암호가 1234인 user kim에게 test 데이터베이스의 모든 테이블에 대한 모든 권한을 주고 싶을 때,

    grant all on test.* to kim identified by '1234';


-------------------------------

#3. DML (Data Manipulation Language)

##스칼라 함수

###substr

    select ename, substr(ename, 1, 3) from emp;


###concat

    select concat(ename, '(', job, ')') from emp;

oracle에서는 || 연산자를 사용한다.


###abs

    select abs(-123);

oracle에서는 반드시 *select abs(-123) from dual;* 처럼 table명을 써줘야하는데 mysql은 그렇지 않다.


###round, ceil, floor, truncate

    select ename, sal/3, round(sal/3), ceil(sal/3), floor(sal/3), truncate(sal/3, 0) from emp;


###left, right

    select job, left(job, 2), right(job, 2) from emp;


###reverse

    select ename, reverse(ename) from emp;


###now, curtime

    select now(), curtime();

- now(), sysdate(), current_timestamp() : 현재 날짜와 시간
- curdate(), current_date() : 현재 날짜


###year, month, dayofmonth, dayname

    select ename, year(hiredate), month(hiredate), dayofmonth(hiredate), dayname(hiredate) from emp;

year는 연도, month는 월, dayofmonth는 월별 일자, dayname은 요일을 영어로.


###현재까지의 날짜

    select to_days(current_date()) - to_days('1991-07-20');


###date_format
이런 형식으로 출력하려면,
> '17/02/21 (PM)05:33:58 Tue'

    select date_format(now(), '%y/%m/%d (%p)%h:%i:%s %a');


------------------------------------

##논리관련함수

###if

    if(논리식, 참일 때, 거짓일 때)

    select ename, if(deptno = 10,  '인사', if(deptno = 20, '회계', '영업')) 부서명 from emp;

    select ename, if(sal > 3000, '대박', '헐') from emp;


###ifnull

    ifnull(값1, 값2)

값1이 null이면, 값2로. null이 아니면 값1으로.

oracle에서는 nvl(값1, 값2)을 썼다.

    select ename, sal, comm, (sal + ifnull(comm, 0)) * 12 연봉 from emp;


-------------------------

##그 밖의 함수

###limit
index는 0부터!

급여를 많이 받는 사람 3명을 출력 -> index가 3보다 작은 사원들을 출력.

    select ename, sal from emp order by sal desc limit 3;


급여등수가 3,4,5등인 사원 출력 -> index가 2부터 3명을 출력.

    select ename, sal from emp order by sal desc limit 2, 3;


###password

    insert into dept values(50, '총무팀', password('seoul'));

이렇게 되면 50번 부서의 loc column이 알아볼 수 없게 insert된다. 주로 사용자의 password 같이 암호화가 반드시 필요한 경우에 사용한다. 암호화시킨 값 두 개를 비교하고 싶을 때는 암호화된 값끼리 비교해야 한다.


###format

    select ename, format(sal, 0) from emp;
    select ename, format(sal, 1) from emp;

format을 안하면 *7000*으로 출력되는데 format(sal, 0)하면, *7,000*으로 출력된다.
