# Section 2 Project

## 개요
해당 프로젝트는 [코트스테이츠](https://github.com/codestates) AI 부트캠프 Section 2에서 학습한 내용을 활용하기 위해 진행되었습니다.

## 주제 : FIFA Online 4 출시 예정 선수들의 OP 여부 예측
* 수행자 : 장건희
* 기간 : 2023.4.7 ~ 2023.4.12
* 사용 데이터 : [FIFA Online 4 선수 정보](https://fifaonline4.nexon.com/datacenter), [FIFA Online 4 Open API](https://developers.nexon.com/fifaonline4)
* 분석환경 : MacBook Air (M1, 2020)
* 분석도구 : Colab Python 3.9.16, Anacoda 4.10.3 Python 3.7.7
* 주요내용 : 분류 모델
* * *

## 1. 프로젝트 배경 및 필요성

#### FIFA Online 4 급여 시스템
- 급여
  - 유저가 팀에서 선수를 사용하기 위해 지불해야 하는 게임 자원
  - 모든 유저는 자신의 팀에 대해서 사용할 수 있는 급여의 최대치가 동일하다.
  - 좋은 능력을 가진 선수일수록 더 많은 급여를 필요로 한다.
- 즉, 급여 시스템은 유저가 사용하는 팀의 선수들이 지나치게 강력해져 유저 간 팀의 균형이 무너지는 것을 막는 시스템이다.

#### FIFA Online 4 선수 영입 방법
- 일반적으로 다른 유저가 경매장에 등록한 선수를 게임 재화를 통해 구매한다.
- 매물이 존재하지 않는 희귀 카드나 신규 카드의 경우, 뽑기 시스템을 통해 확률적으로 획득 가능하다.

#### 신규 선수에 대한 밸런스 조정을 지양하는 분위기
- 신규 선수는 일반적으로 기존의 선수들에 비해 더 좋은 성능을 지닌다.
- 선발대(랭커, 과금러, 고인물)는 신규 카드 출시 시 많은 돈을 지불하더라도 신규 선수를 획득하고자 한다.
- 신규 선수가 유저들의 과금을 유도하는 만큼, 게임사 측에서는 신규 선수 출시 이후 이들에 대한 밸런스 조정을 최대한 지양한다.

#### 신규 선수가 지나치게 강력할 경우 초래하는 문제
- 대부분 유저
  - 게임 내 유저 간 밸런스가 무너지고, 지나친 과금 유도를 유발하기 때문에 반발이 발생한다.
  - 게임이탈, 불매운동으로 이어질 수 있다.
  - 이를 방치하면 다수의 유저가 게임에서 이탈하기 때문에 게임의 지속성에 치명적이다.
- 일부 선발대
  - 이미 신규 선수를 획득하기 위해 많은 돈을 지불한 만큼, 밸런스 조정을 원치 않는다.
  - 밸런스 조정이 이어지더라도, 그들이 지불한 금액에 맞는 합당한 대가를 요구한다.
  - 적절한 보상이 주어지지 않는다면, 게임이탈과 불매운동으로 이어질 수 있다.
  - 이들은 소수지만 게임사 수익에 많은 비율을 차지하는 만큼, 게임의 수익성에 치명적이다.
- 따라서 게임사는 많은 유저층의 불만을 해소하기 위해 신규 선수의 성능을 낮출 수 밖에 없다.
- 신규 선수의 성능을 낮춘다고 하더라도, 이로 인해 새로운 불만이 생기는 것은 불가피하다.
- **따라서 출시 전에 미리 과도한 성능을 가진 선수를 예측하고 급여를 통해 성능을 조정할 필요가 있다.**

#### 이에 본 프로젝트에서는 출시 예정 선수의 OP 여부를 예측하여 앞선 문제들이 발생하는 것을 예방하고자 한다.

## 2. 분석 개요
<p align="center"><img src = https://i.imgur.com/0PrS47v.png width="1000" height="300"/> </br>


## 3. 분석 준비
**데이터 수집**
- FIFA Online 4 데이터 센터에서 제공하는 선수 정보 크롤링
  - `선수고유번호, 선수이름, 포지션, 신장, 몸무게, 총 능력치` 등 각 선수와 관련된 데이터 수집하여 분석에 사용할 `선수 데이터` 생성
- Nexon 개발자센터에서 제공하는 FIFA Online 4 Open API 활용
  - `메타정보(선수고유번호, 경기타입)`, `TOP 10000 랭커 유저가 사용한 선수의 20경기` 수집

**타겟 변수 생성**
- `TOP 10000 랭커 유저가 사용한 선수의 20경기`를 바탕으로 랭커들이 많이 사용하는 선수 정보 추출
- 랭커들이 많이 사용하는 선수를 OP 선수라고 가정
- `선수 데이터`에 `OP 여부`칼럼을 생성하고 랭커들이 많이 사용하는 선수에 대해서 `1`, 아니면 `0` 값을 부여 (Boolean Type)

**데이터 전처리**
- 불필요한 칼럼 제거 및 범주형 데이터의 카디널리티 축소

**데이터 분리**
- 포지션 별로 OP 여부에 미치는 영향이 다르다고 판단하여 포지션 별로 서로 다른 데이터 생성

## 4. 분석
**분류모델 생성**

  
  
  

## 4. 인사이트 및 한계점



* * *
# 피드백
1. 내가 수집하고 활용한 데이터가 내가 생각했던 내용을 담고 있지 않은 경우가 발생했다.
  - 실제로 이로 인해 분석을 어려 번 수행했고, 대부분의 수행 내용이 최종 결과에 반영되지 못했다.
  - 제출한 내용에서도, 랭커들의 사용 기록 데이터가 내가 생각한 정보를 담고 있지 않다.
    - 아예 잘못된 내용이라고 할 수는 없지만, 내가 생각했던 정보의 일부만을 담고 있다.
  - 향후 계획 : 데이터를 수집했다는 사실에 만족하지 말고, 수집한 데이터가 내가 활용할 수 있는 정보를 담고 있는지 확인한 후 분석으로 넘어가자
  

# 보충 학습  
Project를 진행하면서, 새롭게 알게 된 부분 정리
