# REFERENCE

> SQL 공부하면서 참고사항 정리 



### Rule

- 명령어는 대문자를 사용
- 데이터명은 대/소문자 구별

```sql
SELECT * 
FROM EMPLOYEE;
```



### DUAL

- 함수를 실행할 때 임시로 사용하는데 적합
- 함수에 대한 쓰임을 알고 싶을 때 특정 테이블을 생성할 필요없이 dual 테이블을 이용하여 함수의 값을  리턴 받을 수 있다.

```SQL
FROM DUAL;
```

