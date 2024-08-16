# Deep Learning Project
Introduction
---
무인매장 고객 행동 탐지 모델 개발

프로젝트 개요
---
1. 팀원: 강민지, 김예림, 김이영
2. 수행기간: 2024.07.18 ~ 2024.08.08 (4주)
   
프로젝트 소개
---

프로젝트 진행 순서
---
![Blank diagram](https://github.com/user-attachments/assets/35a56547-a196-4588-aa8d-f85cc90c4ab5)


데이터 수집 & 소개
---

데이터 전처리
---

Mediapipe
---

YOLOv8 & Mediapipe
---

하이퍼파라미터 튜닝
---

모델 평가
---

비즈니스 효과
---

이슈 및 트러블슈팅
---
01. Mediapipe 객체탐지
   - 설명: Mediapipe만을 사용했을 때 객체탐지가 완벽하게 되지 않음. 키오스크를 사람으로 인식하는 경우도 있음.
   - 해결: YOLOv8과 Mediapipe를 함께 사용해 문제 해결
02. FPS
   - 설명: "구매"데이터와 "절도"&"파손"데이터의 FPS가 맞지 않아 데이터 불균형 문제가 발생.
   - 해결: "구매"데이터를 "절도"&"파손"데이터와 같은 3fps로 맞춤.  
03. 영상 길이
   - 설명: 영상들을 각 행동 구간별로 추출해 길이가 맞지 않음. RNN모델은 고정된 입력 크기를 필요로 하기 때문에 오류 발생
   - 해결: max padding을 사용해 데이터의 길이를 100프레임으로 맞춤. 
04. 오버피팅
   - 설명: 오버피팅으로 인해 validation loss가 발산.
   - 해결: 양방형 LSTM, 배치 정규화, 학습률 스케일링을 사용해 오버피팅 문제를 방지.
