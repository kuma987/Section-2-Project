# Section 2 Project

## 개요
해당 프로젝트는 [코트스테이츠](https://github.com/codestates) AI 부트캠프 Section 2에서 학습한 내용을 활용하기 위해 진행되었습니다.

## 주제 : FIFA Onile 4 출시 예정 선수들의 과성능 여부 예측
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
- **따라서 출시 전에 미리 과도한 성능을 가진 선수를 예측하고 미리 성능을 조정할 필요가 있다.**

#### 이에 본 프로젝트에서는 출시 예정 선수의 성능이 지나치게 강력할 지 미리 예측하여 앞선 문제들이 발생하는 것을 예방하고자 한다.

## 2. 분석 개요

<p align="center"><img src = https://i.imgur.com/0PrS47v.png width="1000" height="400"/> 

