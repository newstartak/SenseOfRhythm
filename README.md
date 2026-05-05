# Sense of Rhythm

Sense of Rhythm은 AR 마커를 현실의 버튼처럼 활용하여, 타이밍에 맞춰 손을 올려 리듬 객체를 제거하는 AR 리듬 게임입니다.

상명대학교 산학협력프로젝트로 제작한 프로젝트로, AR 마커 인식, 마커 가려짐 상태 감지, AR Raycast, 3차원 현실 공간에서의 거리 계산 등을 구현했습니다.

## 프로젝트 개요

| 항목 | 내용 |
| --- | --- |
| 프로젝트명 | Sense of Rhythm |
| 장르 | AR 리듬 게임 |
| 개발 환경 | Unity |
| 사용 언어 | C# |
| AR SDK | Vuforia Engine, ARCore |
| 담당 역할 | 클라이언트 개발, BGM 작곡, 도트 아트 작업 |

## 게임 소개

플레이어는 화면에 표시되는 AR 리듬 객체가 마커 위치에 도달하는 타이밍에 맞춰 손을 올려 객체를 제거합니다.

AR 마커를 단순한 인식 대상이 아니라 현실 공간에 배치된 입력 버튼처럼 활용하는 것을 목표로 했습니다.

## 주요 구현 내용

## 1. Vuforia DefaultObserverEventHandler 기반 AR 가려짐 상태 감지 구현

Vuforia의 `DefaultObserverEventHandler`를 활용하여 AR 마커가 카메라에 인식되는 상태와 손에 의해 가려지는 상태를 감지했습니다.

AR 리듬 객체가 마커에 가까워졌을 때, 플레이어가 타이밍에 맞춰 손을 올려 마커를 가리면 이를 입력으로 판단하고 객체를 제거하도록 구현했습니다.

| AR 리듬 객체 접근 | 타이밍에 맞춰 손을 올려 제거 |
| --- | --- |
| <img width="683" height="321" alt="image" src="https://github.com/user-attachments/assets/56d893c2-b11c-40e7-a417-00c6d38d55f1" /> | <img width="690" height="326" alt="image" src="https://github.com/user-attachments/assets/a5140398-15ee-4c0d-bf46-95b34503c1b3" /> |

## 2. AR 마커를 활용한 리듬 입력 구조 구현

일반적인 터치 입력이나 키보드 입력 대신, AR 마커의 인식 상태 변화를 입력으로 사용했습니다.

마커가 정상적으로 인식되는 상태에서는 입력이 발생하지 않고, 플레이어의 손이 마커를 가려 인식 상태가 변경되었을 때 리듬 입력이 발생하도록 구성했습니다.

### 구현 방식

| 상태 | 처리 |
| --- | --- |
| 마커 인식 중 | 입력 대기 상태 유지 |
| 마커가 손에 의해 가려짐 | 리듬 입력으로 판단 |
| 리듬 객체가 판정 영역에 있음 | 객체 제거 및 점수 처리 |
| 리듬 객체가 판정 영역 밖에 있음 | 입력 무효 처리 |

## 시연 영상

<p align="center">
  <a href="https://www.youtube.com/watch?v=YD7IQ8spH8Y">
    <img src="https://img.youtube.com/vi/YD7IQ8spH8Y/maxresdefault.jpg" alt="Sense of Rhythm 시연 영상" width="640">
  </a>
  <br>
  <sub>위 이미지를 클릭하면 시연 영상으로 이동합니다.</sub>
</p>
