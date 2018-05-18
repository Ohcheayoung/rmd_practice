practice\_1
================
Ohcheayoung
2018년 5월 18일

library(foreign) \# SPSS 파일 로드 library(dplyr) \# 전처리 library(ggplot2) \# 시각화 library(readxl) \# 엑셀 파일 불러오기

데이터 불러오기
===============

raw\_welfare &lt;- read.spss(file = "Koweps\_hpc10\_2015\_beta1.sav", to.data.frame = T)

복사본 만들기
=============

welfare &lt;- raw\_welfare

head(welfare) tail(welfare) View(welfare) dim(welfare) str(welfare) summary(welfare)

welfare &lt;- rename(welfare, sex = h10\_g3, \# 성별 birth = h10\_g4, \# 태어난 연도 marriage = h10\_g10, \# 혼인 상태 religion = h10\_g11, \# 종교 income = p1002\_8aq1, \# 월급 code\_job = h10\_eco9, \# 직종 코드 code\_region = h10\_reg7) \# 지역 코드

#### 09-2

--------------------------------------------------------------------
--------------------------------------------------------------------

class(welfare*s**e**x*)*t**a**b**l**e*(*w**e**l**f**a**r**e*sex)

이상치 확인
===========

table(welfare$sex)

이상치 결측 처리
================

welfare*s**e**x* &lt; −*i**f**e**l**s**e*(*w**e**l**f**a**r**e*sex == 9, NA, welfare$sex)

결측치 확인
===========

table(is.na(welfare$sex))

성별 항목 이름 부여
===================

welfare*s**e**x* &lt; −*i**f**e**l**s**e*(*w**e**l**f**a**r**e*sex == 1, "male", "female") table(welfare*s**e**x*)*q**p**l**o**t*(*w**e**l**f**a**r**e*sex)

--------------------------------------------------------------------
--------------------------------------------------------------------

class(welfare*i**n**c**o**m**e*)*s**u**m**m**a**r**y*(*w**e**l**f**a**r**e*income) qplot(welfare*i**n**c**o**m**e*)*q**p**l**o**t*(*w**e**l**f**a**r**e*income) + xlim(0, 1000)
