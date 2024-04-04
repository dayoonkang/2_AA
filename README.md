https://github.com/dayoonkang/2_AA/assets/150164152/f4ed45b2-81e7-4679-959f-08d98739855c

# 🎮 AA_2D_Mouseplay
유니티 2D 박자 맞추기 게임 "AA"

## 💻 프로젝트 소개
빙글빙글 돌아가는 원이 있어요. 😵‍💫

N개의 핀을 마우스 클릭을 통해 원에 붙이는 게임이에요. 📍

원은 언제 방향이 바뀔지 몰라요! 왼쪽으로 돌아갈지, 오른쪽으로 돌아갈지도요. 😜

핀끼리는 닿아선 안돼요. 💣🤯

무사히 N개의 핀을 쏘아 올리면 성공!💙 핀끼리 닿으면 실패!❤️

## 🏃‍♀️ 개발 기간
23.11.13 - 23.11.15

## ⚙️ 개발 환경 및 사용 언어
- Window x64
- Unity 2022.3.12f1
- Visual Studio 2022 C#

## 🌟 주요 기능
1. 회전하는 원과 원을 향해 쏘아지는 핀
2. 핀은 마우스 좌클릭으로 발사
3. 핀과 타겟 원의 충돌 처리
4. 동일한 위치에서 여러 개의 핀을 발사할 수 있는 Pin Launcher system
5. 목표 핀 갯수 설정
6. 목표 핀의 달성 여부에 따른 성공/실패 처리
7. 난이도 조절을 위한 rotate animation
8. game over canvas와 retry button

## 💪 이 프로젝트를 통해 무엇을 배우셨나요?
1. 회전하는 원 생성
   - TargetCircle C# Script 생성
   - Update마다 transform.Rotate 함수를 이용하여 회전하게끔 설정
   - RotateSpeed라는 변수를 생성하여 unity에서 속도를 변경할 수 있게끔 설정

2. 위로 이동하는 핀 생성
   - Pin Script를 생성
   - transform.position 함수와 Vector3.up 함수를 이용하여 위로 이동하게 만듦
   - 속도는 moveSpeed 함수를 이용

3. 충돌처리
   - Rigidbody 2D를 사용
   - Gravity scale 조절
   - Is Trigger 체크박스 해제하여 실제 충돌 액션 설정
   - onTriggerEnter2D 함수 사용
   - cast를 활용하여 충돌 대상이 pin인지 확인
   - bool 변수를 설정하여 pinned의 상태 확인
   - 충돌한 target의 transform을 확인하여 pin을 그 위치에 고정
     
4. Parent와 Child Actor의 활용
   - 핀의 꼬리 생성, Pin의 childObject로 설정.
   - transform.GetChild(Index) 함수를 활용하여 꼬리의 위치 설정
   
5. 여러개의 핀 생성
   - PinLauncher라는 새로운 Script 생성
   - Pin class가 PinLauncher를 활용할 수 있게끔 캐스트
   - isLaunched 부울 변수를 생성하여 current pin과 ready pin을 구분
   - 마우스 클릭에 Launch 될 수 있게끔 Input.GetMouseButtonDown 함수 사용

6. 목표 설정
   - Rect Transform을 이용하여 Text의 위치 설정
   - GameManager에서 TMPro 헤더를 선언하고 textGoal을 unity에서 변경 가능하게끔 SerializeField
   - GameManager.instance.DecreaseGoal 변수와 함수를 활용하여 성공한 pin의 갯수가 증가하면 목표 골의 갯수를 감소시킴

7. 게임 오버 처리
   - if 문을 사용하여 if(goal<=0) 시에 SetGameOver 변수의 true/false 처리
   - 성공했을때는 파란색 화면, 실패했을때는 빨간색 화면 -> Camera.main.backgroundColor 함수 활용
   - Canvas에서 button 생성, 게임이 끝났을때 보여주는 로직을 GameManager 에 작성
   - btnRetry 변수를 만들어서 SetActive 변수와 Invoke(1f) 함수를 이용하여 게임이 끝나면 1초 후 true가 되도록 설정
  
8. 난이도 조절
   - Window- Animation을 통해 Rotate Animation 생성
   - Add Property 하여 Rotate Speed의 Frame 값 설정 -> Animation 저장
 

## 💭 나중에 추가하고 싶은 기능
- 핀이 공에 붙을 시 개구진 효과음 플레이
- level system 설정: 회전 방향 변경 횟수, 핀의 갯수, 회전 속도 등이 level에 따라 random upgrade
- level system 시각적으로 확인: 내가 깬 맵과 깨지 못한 맵을 로드맵으로 시각화
- 핀이 제자리에서 생성되는 것이 아니라, 미리 생성되어 순서를 기다리는 핀이 앞으로 쏘아 나가지는 것처럼 디자인
- target circle에 미리 존재하는 핀이 랜덤으로 붙어 있게끔 하여 첫번째로 던지는 pin의 난이도 up

## ✔️ 참고자료
Youtube - 나도코딩 "5000만 다운로드 게임 aa 만들기 - 유니티 게임개발 무료 강의 (실전 프로젝트1)"
