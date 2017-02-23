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

#2. DDL (Data Definition Language)

##create table

    create table sawon (
	     empno int primary key not null auto_increment,
       ename varchar(20),
       age int
    );

*auto_increment* 를 가진 column은 row가 삽입될 때 자동적으로 한 개씩 값이 증가한다. data가 null일 때도 column에 자동적으로 한 개씩 값이 증가하여 삽입된다.

**Foreign Key** 설정은 oracle과 동일하다.

*on delete cascade* 은 row를 삭제할 때 그 자식 row도 한꺼번에 삭제 된다. cascade 설정을 안하면 default는 restrict이다. restrict는 자식 row가 있는 경우 삭제 불가능.

##alter table

    alter table sawon modify ename varchar(40);

위의 쿼리는 sawon table에서 ename이란 column의 자료형을 varchar(40)으로 변경하는 쿼리이다.

    alter table sawon change ename name varchar(30);

위의 쿼리는 sawon table에서 ename이란 column의 이름을 name으로 자료형을 varchar(30)으로 변경하는 쿼리이다.

-------------------------

#3. DCL (Data Control Language)

##권한 부여

    grant 권한 on db명.table명 to user명 [identified by '암호'] [with grant option];

with grant option을 받은 user는 그 권한을 다른 user에게 줄 수 있게 된다.


암호가 1234인 user kim에게 test 데이터베이스의 모든 테이블에 대한 모든 권한을 주고 싶을 때,

    grant all on test.* to kim identified by '1234';


-------------------------------

#4. DML (Data Manipulation Language)

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
>17/02/21 (PM)05:33:58 Tue

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


------------------------------------

#5. Data 백업 및 복구

##1) database 통째로

**백업**

    mysqldump -u root -p test > c:/mysql/test.txt

cmd창에서 위의 명령을 실행하고 password를 입력하면, root user의 test database를 test.txt 파일에 통째로 백업시킨다.


**복구**

    mysql -u root -p test2 < c:/mysql/test.txt

만약 test라는 database가 다 날라갔다면, 백업시켜놓은 text.txt를 다시 어떤 database에 복구하면 된다. 이 명령에선 test2라는 database에 복구하려 한다. 이 때, test2 database는 create 되어있어야 한다.


##2) table만

**백업**

    mysqldump -u root -p world city > c:/mysql/city.txt

world database에 있는 city table을 city.txt에 백업시키는 명령이다.


**복구**

    mysql -u root -p test < c:/mysql/city.txt

백업시킨 city table을 test database에 복구하는 명령이다.


##3) data만

data가 외부에서 올 때, 주로 *,*(콤마)로 구분된 txt file이 오거나, cvs 엑셀파일이 온다. 이 때 data를 load하는 명령문은 다음과 같다.

    load data local infile 'c:/mysql/sawon.csv' into table sawon
    character set euckr
    fields terminated by ','
    lines terminated by '\r\n';

여기서 *\r\n* 은 엔터를 말한다.


---------------------------------------

#6. MySQL Procedure

    drop procedure if exists dept_insert;
    delimiter //
    create procedure dept_insert (vdeptno int, vdname varchar(20), vloc varchar(20))
    begin
      insert into dept values (vdeptno, vdname, vloc);
    end;
    //
    delimiter ;

가장 위의 procedure를 drop하는 명령문은 mysql에서는 oracle과 달리 procedure를 create할 때 create or replace가 아니라 그냥 create만 하기 때문에 이미 있으면 create되지 않기 때문에 사용한다.

delimiter //는 원래 명령문이 끝나는 건 ;(세미콜론)을 만나야 하는건데, //를 만나야 끝나는거라고 바꾼것이다. 그리고 end;하고서 //를 만나는 순간 procedure를 create하는 문장이 끝남을 인식한다. 그 후에 다시 원래대로 delimiter를 ;로 원위치 시킨다.


실행시킬 때에 oracle에서는 exec였는데 mysql은 call로 호출한다.

    call dept_insert(50, '호잇', '서울');

이렇게 dept_insert procedure를 호출하면, 50부서가 dept table에 삽입된다.
