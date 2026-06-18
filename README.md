# AI_Project_1_Group3
## ABIDE 데이터셋 기반 자페 스펙트럼 장애 - Autism Spectrum Disorder (ASD) 분류
## Project 소개
1.  **자페 스펙트럼 장애 - Autism Spectrum Disorder (ASD) 란?**
- 뇌 영역 간의 기능적 과잉 연결(Functional Over-connectivity) 또는 저연결(Functional Under-connectivity)로 인해 발생하는 장애.
- *진단의 필요성*: 
정확한 진단을 위해 뇌의 특정 활동 패턴을 식별하는 객관적 지표가 필요함.

2. **참고 논문**
- *Topological turning points across the human lifespan, Mousley, et al.*
- 뇌의 구조적 연결성(Structural Connectivity - SC)은 32세에 완벽화되어 성인 뇌가 된다.
- 이 논문을 바탕으로 가설을 새월 뇌영역간의 기능적 변화화 구조적 변화의 연결성을 관찰하려고 했다.

 3. **가설** 

   - (a) 32세 이상인 자폐 환자의 뇌기능적 연결성(FC)은 계속 증가하지만 뇌구조적 연결성(SC)은 줄어든다.
   - (b) 32세 이하인 정상인의 뇌구조적 연결성(SC)은 증가하지만 뇌기능적 연결성(FC)은 약해진다.

## 데이터셋 소개
**ABIDE 1 - Autism Brain Imaging Data Exchange 1**

*데이터셋의 구성 및 규모*
- 4D rs-fMRI (시계열 데이터) + CSV data (나이, 성별, ASD : 0 or 1)
- 총 피험자 수: 1,112명
- 자폐 스펙트럼 장애(ASD) 환자군: 539명
- 일반 대조군(Typical Controls, TC): 573명
- 수집 기관(Sites): 전 세계 17개 서로 다른 연구 기관

## 제안 방법
- Graph-based Deep Learning Model 기반 자폐 스펙트럼 장애를 32세 이하/이상 2개의 나이 그룹별로 분류한 결과를 Grad-Cam을 사용해 설명.
1. 초안 제안 방법 : A-GCN model

2. 바꾼 제안 방법 : Cross-Atlas Fusion Model

