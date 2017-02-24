#Table 백업

    exp user명/암호 file=파일명 tables=테이블1명,테이블2명,...

예를 들어, 암호가 tiger인 scott user가 emp table과 dept table을 a.dmp 파일에 백업하고 싶다면,

    exp scott/tiger file=a.dmp tables=emp,dept

exp는 export!


#Table 복구

    imp user명/암호 file=파일명 tables=테이블1명,테이블2명,...

예를 들어, 암호가 tiger인 scott user가 a.dmp파일에 있는 table 두 개를 각각 emp table과 dept table에 복구시키고 싶다면,

    imp scott/tiger file=a.dmp tables=emp,dept

imp는 import!
