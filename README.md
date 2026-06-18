# AI_Project_1_Group3
## ABIDE 데이터셋 기반 자페 스펙트럼 장애 - Autism Spectrum Disorder (ASD) 분류
- 팀원 : 엘몬, 정인호, 양다윗
## 1. Project 소개
**a)  자페 스펙트럼 장애 - Autism Spectrum Disorder (ASD) 란?**
- 뇌 영역 간의 기능적 과잉 연결(Functional Over-connectivity) 또는 저연결(Functional Under-connectivity)로 인해 발생하는 장애.
- *진단의 필요성*: 
정확한 진단을 위해 뇌의 특정 활동 패턴을 식별하는 객관적 지표가 필요함.

**b) 참고 논문**
- *Topological turning points across the human lifespan, Mousley, et al.*
- 뇌의 구조적 연결성(Structural Connectivity - SC)은 32세에 완벽화되어 성인 뇌가 된다.
- 이 논문을 바탕으로 가설을 새월 뇌영역간의 기능적 변화화 구조적 변화의 연결성을 관찰하려고 했다.

 **c) 가설** 

   - (i) 32세 이상인 자폐 환자의 뇌기능적 연결성(FC)은 계속 증가하지만 뇌구조적 연결성(SC)은 줄어든다.
   - (ii) 32세 이하인 정상인의 뇌구조적 연결성(SC)은 증가하지만 뇌기능적 연결성(FC)은 약해진다.

## 2. 데이터셋 소개
**ABIDE 1 - Autism Brain Imaging Data Exchange 1**

*데이터셋의 구성 및 규모*
- 4D rs-fMRI (시계열 데이터) + CSV data (나이, 성별, ASD : 0 or 1)
- 총 피험자 수: 1,112명
- 자폐 스펙트럼 장애(ASD) 환자군: 539명
- 일반 대조군(Typical Controls, TC): 573명
- 수집 기관(Sites): 전 세계 17개 서로 다른 연구 기관

## 3. 제안 방법
- Graph-based Deep Learning Model 기반 자폐 스펙트럼 장애를 32세 이하/이상 2개의 나이 그룹별로 분류한 결과를 Grad-Cam을 사용해 설명.

**a) 초안 제안 방법 : A-GCN model**

**b) 바꾼 제안 방법 : Cross-Atlas Fusion Model**
 - 7 Models : GCN, GIN, GAT, TransformerGNN, ChebConv GCN, Graph SAGE, BrainNetCNN
 - 3 Atlases : AAL-116, CC-200, Schaefer-200
 - 3 Age Groups : All, 청소년 (<18), 성인 (>18)
    *[ 데이터셋의 나이분포와 맞게 18세로 나누었음. 추후에 데이터셋 추가해 32세로 바꾼 예전 ]*

**System Pipeline**
<img width="1184" height="729" alt="image" src="https://github.com/user-attachments/assets/4a951ba0-7150-4e19-a6a7-8da9f697861b" />


## 4. 필요한 라이브러리
- python, pytorch, nilearn
  
## 5. 데이터 확인 (EDA) 및 전처리
- fMRI .nii file
  
  <img width="365" height="264" alt="image" src="https://github.com/user-attachments/assets/d2168bc3-4e9e-4e10-bb3e-879e098a7425" />
  
  <img width="394" height="386" alt="image" src="https://github.com/user-attachments/assets/1122b0ae-f6a8-428f-9f76-845ab1882af4" />


- 나이분포 :

  <img width="346" height="239" alt="image" src="https://github.com/user-attachments/assets/da983be2-186f-4ad4-be6d-6b49733748d8" />

- 성별분포
   light pink - Male,
   pink - Female
   
   <img width="366" height="263" alt="image" src="https://github.com/user-attachments/assets/e2f7690a-f9bf-4829-a2c0-2ab48b5ef2c5" />

- 전처리 (Brain Parcellation) 후 .pt file 확인 및 시각화
  
   <img width="1517" height="646" alt="image" src="https://github.com/user-attachments/assets/0607d989-ce55-45f3-b93e-1c4372200914" />
   <img width="573" height="310" alt="image" src="https://github.com/user-attachments/assets/fb49ac3a-0c39-47fd-8e27-14264713d0e3" />


## 6. 모델 및 성능평가
- Baseline Models

<img width="1390" height="680" alt="image" src="https://github.com/user-attachments/assets/b0226809-ff3d-47f1-a6b5-fec617c404da" />

- Model Comparison

<img width="2228" height="771" alt="model_comparison_plot" src="https://github.com/user-attachments/assets/da462b44-2b00-4f57-8178-e58e0f718553" />

- 나이별 최적 Model

<img width="1324" height="791" alt="image" src="https://github.com/user-attachments/assets/a7590beb-c94f-4451-9eb1-8114618f6c15" />

- Cross-Atlas Fusion Model

<img width="558" height="132" alt="image" src="https://github.com/user-attachments/assets/b54f75e5-7a47-4de3-98d0-fbbab8315ff3" />

## 7. 결론 및 추후 계획
- Model performance 의 원인 fMRI data 전처리 (Brain Atlas Parcellation)방법 AAL, CC, Schaefer 를 100, 200, 400 등 다양하게 해보고 적절한 Atlas석택이 필요.
- 데이터 특성상 18세로 나누었지만 실제로 32세로 나눌 수있게 맞는 데이터 추가 필요.
- Cross-Atlas Fusion 외에 Self-supervised Learning 등 더 다양한 학습방법과 model을 시도할 필요.
