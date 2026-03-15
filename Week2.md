# SQL_BASIC 2주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_2nd_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**2주차 과제**는 1주차 과제처럼 SQL의 필요성이나 느낀점 위주가 아닌, **실제 강의 내용을 바탕으로 개념을 정리하고 학습한 내용을 집중적으로 기록**해주세요. 완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요. 

**👀(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_2nd

### 섹션 3. 데이터 탐색 - 조건, 추출, 요약

### 2-3. 데이터 탐색 (SELECT, FROM, WHERE)

### 2-4. SELECT 연습문제

### 2-5. 집계 (Group By + Having + Sum/Count)



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | 🍽️         |
| 4주차 | 섹션 **3-4** ~ **4-4** | 🍽️         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리 

## 2-3. 데이터 탐색 (SELECT, FROM, WHERE)

~~~
✅ 학습 목표 :
* SQL 쿼리 구조를 이해할 수 있다. 
* SELECT, FROM, WHERE의 핵심 문법을 설명할 수 있다. 
~~~

- 쿼리를 작성할 때 기본적으로 알아야 하는 것은 SELECT, FROM, WHERE
SELECT: 
- table의 어떤 컬럼을 출력할 것인가
- Table에 저장되어 있는 컬럼 선택
- 여러 컬럼 명시 가능
- col1 AS “별칭”으로 컬럼의 이름도 별칭 지정 가능
예) 예) id AS pokemon_id,
- *: 모든 컬럼을 출력하겠다

  FROM: 
- 어떤 table에서 데이터를 확인할 것인가 예) 포켓몬 테이블
- 데이터를 확인할 table 명시
- 이름이 너무 길다면 AS (컬럼명) 으로 컬럼명 수정하기

WHERE: 
- 만약 원하는 조건이 있다면 어떤 조건인가? 예) name=꼬부기
- FROM에 명시된 table에 저장된 데이터를 필터링
- table에 있는 컬럼 조건 설정

쿼리 구조
SELECT
  컬럼1,
  컬럼2,
  컬럼3,
FROM 테이블
WHERE
  <조건문>

예)SELECT
  id AS pokemon_id,
  kor_name,
  type1,
  total,
 FROM `basic.pokemon`
 WHERE
  type1 = “Fire”;

## 2-5. 집계 (Group By / HAVING / SUM,COUNT)

~~~
✅ 학습 목표 :
* 데이터를 집계하고 그룹화하는 방법을 설명할 수 있다.
* GROUP BY, HAVING, ORDER BY, 집계함수(SUM/COUNT 등)을 활용하는 방법을 설명할 수 있다.
* having과 where의 차이에 대해서 설명할 수 있다.
~~~

GROUP BY: 같은 값끼리 모아서 그룹화하기
DISTINCT: 여러 값 중에서 중복을 제거하는 것
ORDER BY: 정렬하기, 마지막에 작성
LIMIT: row 수 제한하기

그룹화를 자주 사용하는 경우
- 일자별 집계
- 연령대별 집계
- 특정 제품 타입별 집계

SELECT
  집계할 컬럼1,
  집계 함수(COUNT, MAX, MIN 등)
FROM Table
GROUP BY
  집계할 컬럼1

예) 
SELECT
  type1,
  AVG(attack) AS avg_attack,
  Count(id) as cnt
FROM Pokemon
GROUP BY
  type1

WHERE: 처음에 table에 조건을 바로 걸 경우
HAVING: GROUP BY한 후 조건을 설정하고 싶은 경우 사용

예)
SELECT
  컬럼1, 컬럼 2
  COUNT(컬럼1) AS col1_count
FROM Table
GROUP BY 컬럼1, 컬럼 2
HAVING 
  col1_count>3

# 2️⃣ 학습 인증란
<img width="1918" height="908" alt="Image" src="https://github.com/user-attachments/assets/a0d8c51f-ca52-4acc-a281-32ba6d4524ee" />




<br><br>



---

# 3️⃣ 확인문제

## 문제 1

> **🧚Q. 포켓몬 마스터 진아는 포켓몬 데이터 조회하는 SQL문에 재미를 느껴서 혼자서 데이터를 조회하는 쿼리문을 짰습니다. 하지만 세 가지의 오류로 다음 코드가 실행이 안된다고 하는데, 각 오류의 위치와 이유를 설명하고, 올바른 쿼리문으로 수정해보세요.**

~~~sql
# 진아의 SQL Query문 
SELECT name. type
FROM pokemon;
WHERE type = Electric;
~~~



~~~
첫 번째 행: name 우측 마침표가 아닌 쉼표, 
두 번째 행: 세미클론은 한 퀴리가 마무리 될 때 사용하므로 pokemon 우측 세미클론 제거
세 번째 행: Electric라는 조건을 걸기 위해서 양 옆에 “”표시 필요

SELECT 
  name, type,
FROM pokemon
WHERE type = “Electric”;
~~~



## 문제 2

> **🧚Q. 앞서 SQL Query의 오류를 해결한 진아는 기분 좋게 이번에는 포켓몬 데이터에서 타입별 평균 공격력이 60 이상인 타입만 조회하려는 쿼리를 작성하려고 했습니다. 하지만 이번에도 실수를 하여 쿼리문이 실행되지 않거나 잘못된 결과가 나오고 있는데, 쿼리에서 잘못된 부분이 무엇인지 설명하고, 올바르게 수정한 쿼리를 작성해보세요.**

~~~sql
SELECT type, AVG(attack) AS avg_attack
FROM pokemon
WHERE AVG(attack) >= 60
GROUP BY type;
~~~



~~~
WHERE은 테이블 초반에 조건을 설정할 때 사용하기에, 해당 퀴리에서는 GROUP BY 이후 4번재 행에 HAVING으로 조건을 걸어야 한다.
SELECT 
  type, 
  AVG(attack) AS avg_attack
FROM pokemon
GROUP BY type
HAVING AVG(attack) >= 60
~~~



### 🎉 수고하셨습니다.
