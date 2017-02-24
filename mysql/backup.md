#Data 백업 및 복구

##1. database 통째로

**백업**

    mysqldump -u root -p test > c:/mysql/test.txt

cmd창에서 위의 명령을 실행하고 password를 입력하면, root user의 test database를 test.txt 파일에 통째로 백업시킨다.


**복구**

    mysql -u root -p test2 < c:/mysql/test.txt

만약 test라는 database가 다 날라갔다면, 백업시켜놓은 text.txt를 다시 어떤 database에 복구하면 된다. 이 명령에선 test2라는 database에 복구하려 한다. 이 때, test2 database는 create 되어있어야 한다.


##2. table만

**백업**

    mysqldump -u root -p world city > c:/mysql/city.txt

world database에 있는 city table을 city.txt에 백업시키는 명령이다.


**복구**

    mysql -u root -p test < c:/mysql/city.txt

백업시킨 city table을 test database에 복구하는 명령이다.


##3. data만

data가 외부에서 올 때, 주로 *,*(콤마)로 구분된 txt file이 오거나, cvs 엑셀파일이 온다. 이 때 data를 load하는 명령문은 다음과 같다.

    load data local infile 'c:/mysql/sawon.csv' into table sawon
    character set euckr
    fields terminated by ','
    lines terminated by '\r\n';

여기서 *\r\n* 은 엔터를 말한다.
