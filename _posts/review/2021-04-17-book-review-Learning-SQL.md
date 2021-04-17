---  
title: "[Book Review] Learning SQL"  
categories: Review  
tag:
  - SQL
  - MySQL
  - Structured Query Language
  - 쿼리
  - O'REILLY
date: 2021-04-17
last_modified_at: 2021-04-17
---  

데이터 생성, 검색, 조작까지 데이터 제대로 주무르기

---

![나는 리뷰어다 2021](/assets/images/I-am-reviewer.jpg)

## Book Info

[![책](/assets/images/review/Learning-SQL.jpg)](http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9791162244074&orderClick=LEa&Kc=)

- 제목: 수학과 함께하는 AI 기초
- 저자: Alan Beaulieu
- 역자: 류수미, 송희정
- 출판사: 한빛미디어
- 출간: 2021-03-30

## 이 책을 읽게 된 이유

이 책은 한빛미디어에서 진행하는 `나는 리뷰어다 2021`에 참여하게 되어 읽게 됐습니다. 3월 리뷰처럼 이번 4월 리뷰에도 좋은 책들이 많았고, 저는 많은 책들 중 `러닝 SQL`, `몽고DB 완벽 가이드 3판`, `이것이 안드로이드다 with 코틀린(개정판)`을 선택했었습니다.

SQL이든 NoSQL이든 데이터베이스 공부는 필요하다고 생각했기에 선택했습니다. 최근 선형대수학, 통계학, 파이썬 라이브러리 공부 등을 한다고 조금 미뤄졌었지만, 데이터 분석 또는 머신러닝 분야에서 사용할 수 있을 거란 생각에 나중에는 꼭 공부해보고 싶었던 분야 중 하나였습니다.

코틀린은 나중에 졸업작품을 만들 때 안드로이드 앱 개발이 필요할 수 있다고 생각하니 공부를 해보고 싶었고요. 특히 최근에는 코틀린이 안드로이드 이외에 백엔드에도 쓰이고 있다고 들어서 선택했습니다. 

이 책들 이외에도 클라우드 네이티브, 이것이 데이터 분석이다, 배워서 바로 쓰는 14가지 AWS 구축 패턴 등 좋은 책들이 많았습니다.

위와 같은 이유들이 있었지만 결국에는 `러닝 SQL`이 선택되어 대략 2주간 이 책만 보면서 공부했습니다. 

## 간단한 책 소개

이 책은 제목에서도 보셨다시피 SQL을 공부하는 책입니다. MySQL, ORACLE DATABASE, IBM DB2, Microsoft SQL Server, PostgreSQL 같이 SQL은 종류가 많지만, 이 책은 이 중 MySQL을 중점으로 설명합니다. 가끔 MySQL 이외의 SQL 예제들이 나오기도 합니다.

![나는 리뷰어다 2021](/assets/images/mysql-environment-katacoda.jpg)

SQL 예제들은 테이블을 직접 생성하여 사용하기도 하지만, 대부분 sakila database를 사용합니다. sakila database를 다운받아 환경을 구성하는 것을 어려워하는 사람들을 위해 이 책의 원서 출판사인 O'REILLY에서 운영하는 [Katacoda](https://www.katacoda.com/)라는 실습 환경을 제공해줍니다.

![나는 리뷰어다 2021](/assets/images/mysql-environment-wsl2.jpg)

이외에도 환경을 구축할 수 있는 사람은 스스로 환경을 구축하여 책의 예제를 따라 하며 실습을 진행할 수 있습니다. 개인적으로 저는 WSL2(Windows Subsystem for Linux 2)를 사용하여 MySQL 환경을 구축했습니다. 처음에는 Windows에서 MySQL을 사용하려 했으나 이 책은 터미널에서 쿼리를 작성하는 환경을 사용하기 때문에 Workbench를 사용하지 않고 터미널에서 실습을 진행했습니다.

