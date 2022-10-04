# C-AIB-Project
[Codestates] AIB 기업 협업 프로젝트 일리오

# 프로젝트 제목
실시간으로 대화 반응을 수집하고 파악하여 제공하는 서비스.


# 목차
1. [프로젝트 개요](#프로젝트-개요)
2. [프로젝트 구성](#프로젝트-구성)
3. [프로젝트 내용](#프로젝트-내용)
4. [프로젝트 보완점](#프로젝트-보완점)


# 프로젝트 개요

기업 일리오와 협업한 프로젝트로 기업 측에서 요구한 두 가지 사항 **‘⒧ 셀럽의 활동 방향성 제시 ⑵ 셀럽 마케팅 포인트’**를 충족하기 위해 자연어 모델을 제작했다.

1. 셀럽의 활동 방향성 제시
    1. 자연어 감정 분석 모델을 제작해 팬들의 답장에 어떤 감정이 들어있는지 확인 가능.
2. 셀럽 마케팅 포인트
    1. 자연어 축약 모델을 제작해 셀럽에게 대화 가이드 라인을 제시.

# 프로젝트 진행

### 조원

오유리나, 이주현

- 자연어 감성 분류 모델 / 텍스트 요약 데이터 수집과 설계, 발표 자료 제작 및 발표.

데이터 수집, EDA, 모델링, 모델 튜닝 순서로 진행.

### 배경

- 한 명의 셀럽과 다수의 팬이 소통하는 1:다 형식 어플리케이션.
    - 셀럽의 팬 집단이 크면 반응 파악이 어려워져 소통이 힘들어진다는 단점.
    
    → 자연어 모델링을 통해 단점을 극복해 기업 측 요구사항 충족..

- 비슷한 계열의 어플리케이션 ‘버블’
    - 월 구독 4,500원 유료 서비스.
    - 글자수 제한.
    

### 목적

1. 셀럽이 전송한 문장에 대한 팬들의 반응을 실시간으로 수집·파악한다.
2. 보낸 문장에 대한 감정의 척도와 문장의 비율 등 축약된 정보를 셀럽에게 전달해 대화 방향을 제시한다.

# 제작

1. 팬들의 감정을 실시간으로 파악할 수 있는 **‘자연어 감성 분류 모델’**
2. 대화의 방향을 제시하는 **‘텍스트 요약’**

## 자연어 감성 분류 모델

- 형태소 분석기
    - Okt(Open Korean Text), Mecab.
- 데이터 세트
    - 네이버 영화 리뷰 데이터, 네이버 쇼핑 리뷰 데이터, 스팀 리뷰 데이터
    - 한국어 연속적·단발적 통합 대화 데이터 세트

### 리뷰 데이터

1. Okt 형태소 분석기 (LSTM)
    1. 정확도 50% - 데이터 세트 이용 목적이 달라 검증 정확도 떨어진다 판단.
2. Mecab 형태소 분석기 (GRU)
    1. 정확도 87.26% - 실제 제공된 데이터에서 괜찮은 분류를 보여줌.

### 한국어 연속적·단발적 통합 데이터

1. Okt 형태소 분석기 (LSTM)
    1. 정확도 75.51%
2. Mecab 형태소 분석기 (GRU)
    1. 정확도 90.34%
    
    <aside>
    💡 해당 데이터는 7가지 감정 분류로 되어 있어 행복 분류는 긍정, 그외 분류는 부정으로 분류.
    데이터 세트 라벨 균형이 맞지 않아 Weight balancing 진행.
    
    </aside>

# 기대효과

1. 반응 실시간 파악으로 전략적 팬 관리 가능.
2. 대화 주제를 제시하여 1:다 형식이 아닌 1:1 형식 대화로 느끼게 해 만족감.

# 프로젝트 회고

1. 데이터 분류
    1. 긍정 / 부정 만이 아닌 45~65% 데이터는 중립으로 설정.
2. 앙상블 모델 제작
    1. 더 많은 모델을 제작해 앙상블 할 수 있다면 검증 정확도가 높아질 것으로 예상.
3. 자연어 축약 모델 제작
    1. 한국 자연어 축약 모델에 관련된 내용이 적어 시간 관계상 TextRank로 대체.
4. 데이터 세트
