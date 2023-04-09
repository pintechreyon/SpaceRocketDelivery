# 🚀**Space Rocket Delivery**

## 팀 이름: **우리가 고티라고 생각하면 그게 고티 아닐까?**

---

# **빌드파일링크**
- https://www.notion.so/SPACE-ROCKET-DELIVERY-fdc11348621540319c6773fe12f1a832

---

## **기획 의도**

개인 방송 플랫폼과 커뮤니케이션 앱의 보편화로 게임 내에서 얻을 수 있는 재미 뿐만 아니라 타인과 함께 즐기는 재미도 중요해졌다. 그러므로 협동 플레이 요소와 타일 생성이라는 자유도를 통해 게임의 본연의 재미와 소통 및 협동의 재미를 제공하는 게임을 만들고자 한다.<br>



# 세부 기능



SCM
프로젝트의 상태관리를 위해 plastic SCM 리포지토리를 만든 후 6명 모두 참여되었다.<br>



### **캐릭터 및 캐릭터 애니메이션 구현**

![캐릭터](/images/character.png)

원하는 캐릭터 모습이 있는 유니티 에셋을 불러온 후 앞뒤, 좌우 움직임에 대한 애니메이션과 물체를 들어올리는 애니메이션을 구현하였다. <br>
캐릭터의 방향이 바뀔 때 몸체를 회전하는 속도를 지정해주어 어떤 느낌으로 방향을 전환할 지 정할 수 있었다.
<br>

### 자원 나르기

![resource](https://lab.ssafy.com/s08-metaverse-game-sub2/S08P22E206/uploads/567080b37edf0dc3db92ef469e3d6b13/resource.gif)


<br>

### 모듈 수리

![REPAIR](https://lab.ssafy.com/s08-metaverse-game-sub2/S08P22E206/uploads/567080b37edf0dc3db92ef469e3d6b13/resource.gif)

<br>

### **우주선의 움직임 표현 구현**

![우주선](/images/spaceship_background.png)
우주선이 움직이는 것이 아니라 배경이 움직임으로써 우주선의 움직임을 표현하였다.<br>
우주선의 방향이 바뀜을 표현하기 위해 배경이 방향을 틀어서 움직이는 것을 구현하였다. 이 때 방향 벡터는 우주선을 기준으로 z축의 -(마이너스)방향으로 설정해주어야만 했다.
<br>

### **캐릭터 상호작용에 따른 타일의 추가 생성**

![타일생성](/images/character_tiles.png)
캐릭터가 타일의 벽면 쪽으로 가까이 가게되면 새롭게 타일을 생성할 수 있는 청사도가 보여야 한다. <br>
미리 21x21의 타일을 깔아 둔 후, 중앙의 3x3 타일을 제외하곤 모두 투명한 상태로 둔다. 타일을 생성하고자 하는 방향의 벽면에 다가가면 충돌을 감지하여 생성가능한 타일의 투명한 상태를 해제하여 생성가능함을 보여준다. 유저가 생성버튼을 누를 경우 리소스 폴더에 있는 프리팹을 불러와서 생성한다.

<br>

### **캐릭터 상호작용으로 타일 생성 구현**

![타일생성](/images/타일생성.gif)
우주선 외곽에 플레이어가 다가가면 설치할 수 있는 타일의 청사도가 보이고 SPACE를 눌러서 타일을 설치할 수 있다.

<br>

### **우주선 움직임 구현 및 게임 배경 제작**

![게임배경1](/images/게임배경1.PNG)

<br>

![게임배경2](/images/게임배경2.PNG)

구매한 에셋과 제공된 에셋들을 조합하여 난파된 배들과 소행성 지역들을 구현하였다.

몇 가지 방법으로 우주선이 움직이는 것을 표현하였다.

- 배경이 정해진 좌표 값을 기준으로 움직임을 바꾸는 방법
- 우주선이 정해진 좌표 값을 기준으로 움직임을 바꾸는 방법
- 웨이포인트를 정해둔 후 우주선이 웨이포인트까지 가는 방법
- 웨이포인트를 정해둔 후 배경이 웨이포인트까지 가는 방법
- Bézier Path Creator 에셋으로 경로를 만들고 우주선이 그 경로를 따라가는 방법

현재 Bézier Path Creator로 우주선의 움직임을 구현하였으나 다른 팀원과의 Merge 후 오류가 생기고 움직임이 자연스럽지 않아서 배경이 Bézier Path를 따라 움직이는 것으로 변경 중에 있다.

![우주선움직임](/images/우주선움직임.gif)

<br>

### **적 생성 구현 및 적 근접 충돌**

![적공격](/images/적공격.gif)

우주선 주위에 적들이 생성되고, 생성된 적들이 우주선을 향해 돌진하여 공격하는 방식으로 구현하였다. <br>
우주선과 충돌할 경우 우주선은 데미지를 입으며 충돌한 적은 사라진다. <br>
적의 에셋은 새롭게 설정할 예정이며 데미지 계산은 아직 진행되지 않았다. <br>
충돌시 흔들림 효과가 생성되도록 하였다.



<br>

### **적의 공격**

![적_요격](/images/적_요격.gif)

근거리 공격을 하는 적은 우주선에 닿게 되면 충돌하여 데미지를 준다. <br>
원거리 공격을 하는 적은 우주선에서 일정 거리를 둔 후 투사체를 날려서 공격을 한다.
공격 받은 타일은 불이 나는 이펙트가 난다.




<br>

### **레이저 포탑 회전 및 공격**

![레이저포탑](/images/레이저공격.gif)

레이저 포탑이 실시간으로 가장 가까이에 있는 적을 찾아내어 공격한다. <br>
레이저 포탑의 포탑 회전 속도와 각도를 지정하여 특정 회전 속도로 회전하되, x축과 y축 기준으로는 특정 회전 각도 이상 회전하지 못하도록 만들었다.




<br>

### **기본포탑**

![기본포탑](/images/기본포탑.PNG)

플레이어가 직접 조종할 수 있는 포탑


#### 탑승 시

![basic_shooter](/uploads/542fbd9f255f1a684ddde72da7487158/basic_shooter.gif)


<br>

### 산소발생기

![산소발생기](/images/산소발생기.PNG)

지속적으로 관리하지 않으면 고장나고, 고장날 경우 산소가 공급되지 않아 게임오버가 된다.



#### 산소게이지

![O2](/uploads/bed4c8114607f681ede4bba63bb64215/O2.png)

<br>

### **보급기**

![보급기](/images/new_보급기.PNG)

보급기에서 지속적으로 자원이 생성 가능하다.<br>
플레이어가 보급기에 접근하여 SPACE 키를 누르는 것으로 생성되는 자원을 바꿀 수 있다.


### **제작기**

![제작기](/images/new_제작기.PNG)

생산을 위해 필요한 자원과 이미 들어가있는 자원이 표시된다.


### 샷건 포탑

![shotgun](/uploads/ce425ebed3209f3d24998fbbdcb944c9/shotgun.gif)

한 번에 넓은 범위로 공격을 하는 포탑



### 쉴드

![shield](/uploads/a50bfb9e16c88943ac7ca9cb7aeb9b32/shield.png)

범위 내 적의 공격을 막아주는 모듈



### 업그레이드 키트

포탑들의 성능을 향상시켜주는 업그레이드 키트



### 연구소

![lab](/uploads/39bcbde2fd18b1d525c0f1e2cb291dc5/lab.png)

특정 위치에 도달하면 연구소에서 우주선의 기본 능력들을 향상시킬 수 있다.



### 점수 / 도움말 / 게임오버

![TUTORIAL](/uploads/ec2751107ab42274b670c8e6ec12efc1/TUTORIAL.png)

![GAMEOVER](/uploads/7b48f703a96770545ea54824006b400c/GAMEOVER.png)


### 배경음악 추가









### 





## **서버**

클라이언트와 통신을 확인

![서버통신](/images/서버.png)

### 구조 개요

iocp 구조로 비동기 소켓을 관리하며 메세지 처리를 쓰레드 풀에 할당시킴

유저 소켓과 같이 오브젝트가 여러개 있는 경우 불필요한 동적할당과 해제가 발생할 수 있어 오브젝트 풀을 구현해 동적할당을 최소화



### 직렬화

클라이언트 - 서버간 원격 함수 호출을 위해 메세지 타입을 정의, 어떤 메세지던지 첫 바이트를 읽어
메세지 타입을 확인 후 서버에서 알맞은 함수를 호출하도록 일반화 시킴

메세지에는 직렬화된 객체나 변수를 순서대로 기록함
int같은 고정형 변수는 일정 크기만큼 기록해주고,
string같은 가변형 변수는 그 크기를 먼저 기록해 주고 이후에 실제 데이터를 기록해줌
한 메세지에 여러 객체가 들어갈 경우를 대비해 메세지에 한 객체를 통채로 직렬화해 기록해줌

직렬화 동작의 일반화를 위해 클래스 멤버 변수를 알 수 있도록(c++은 직접 구현해야됨) 자체적인 리플렉션 시스템을 구축해 어떤 객체던 직렬화 , 역직렬화가 가능함



### 메세지 처리

```c++
//메세지 기록용 객체
InputMemoryStream inputStream(pOverlapped->m_dataBuffer,static_cast<uint32_t>(transferred));
PacketType pt = PacketType::NONE;
//역직렬화
void* ret = Read(&inputStream,pt);
```

Read([in]stream , [out] PacketType) 함수로 직렬화된 결과물을 보이드 포인터로 반환
output으로 나온 PacketType을 확인해 알맞은 객체의 포인터로 typecast 후 알맞은 함수를 실행

```c++
switch(pt){
    case PacketType::MOVE:
        {
            Move * c = static_cast<Move*>(ret);
            roomManager->moveUser(c);
        }
        break;	
    case PacketType::START_GAME:
        {
             string * c = static_cast<string*>(ret);
             roomManager->startGame(c);
        }
        break;
```


<br>

### 방 생성 / 참가


![LandingPage](/uploads/3e6daadc0c8d5e02b1fd26eb8573fcc0/LandingPage.png)


![waitingroom](/uploads/231281b91cedd04ff0ea7e56d0dc4156/waitingroom.png)


### 멀티플레이


![multiplay](/uploads/4d87b022b57e9803c2984c3a1fe7c168/multiplay.gif)




## 🔖 Convention

### Plastic 브랜치 컨벤션(예시)

#### Branch 종류

- main

  - 배포 가능한 상태의 결과물

- develop

  - 구현한 기능을 병합하기 위한 브랜치
  - 통합 폴더의 기능

- feature

  - 개별 기능 구현 브랜치

  - develop 브랜치에서 분기

  - 개발 후 develop 브랜치로 PR

  - 네이밍 규칙

    ```markdown
    feature-name(기능 이름을 바로 브랜치 이름으로)
    
    # 브랜치 생성 시 한글 사용 금지: 심한 경우 플라스틱 SCM 강제 종료
    # 기능 이름을 직관적으로 알아볼 수 있도록 단어 조합해 브랜치 이름으로 사용
    
    <!-- 실제 예시 -->
    
    characterAnimation
    ```



### Plastic 커밋 컨벤션(예시)

#### 타입

타입은 태그와 제목으로 구성되고, 태그는 영어로 쓰되 첫 문자는 대문자로 작성

**“태그: 제목”의 형태이며, : 뒤에만 space가 있음에 유의**

| 태그 이름                                                    | 설명                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Add                                                          | 파일을 추가하는 작업을 수행한 경우                           |
| Feat                                                         | 새로운 기능을 추가할 경우                                    |
| Fix                                                          | 버그를 고친 경우                                             |
| !BREAKING CHANGE                                             | 커다란 API 변경의 경우                                       |
| !HOTFIX                                                      | 급하게 치명적인 버그를 고쳐야하는 경우                       |
| Refactor                                                     | 프로덕션 코드 리팩토링, 새로운 기능이나 버그 수정없이 현재 구현을 개선한 경우 |
| Docs                                                         | 문서를 수정한 경우                                           |
| (Docs의 경우 http://README.md 수정 등에 해당)                |                                                              |
| Chore                                                        | 빌드 태스트 업데이트, 패키지 매니저를 설정하는 경우(프로덕션 코드 변경 X) |
| (Chore의 경우 package.json의 변경이나 dotenv의 요소 변경 등, 모듈의 변경에 해당) |                                                              |
| Rename                                                       | 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우           |
| Remove                                                       | 파일을 삭제하는 작업만 수행한 경우                           |

```c#
예시
Feat: 캐릭터 움직임
```







## **🎞 발표자료 및 빌드 파일 노션 링크**

https://www.notion.so/031a0972917349e299f5c3959bf5040c



## 🧾 기능명세서 링크

https://www.notion.so/4f61b6d63b34422588bcea33a6a7eb1d



## 📋 API 명세서 링크

https://www.notion.so/API-0ec863edf3de45b8a43d7685e700c09b



---


### ✏ 역할


| 팀원명           | 담당 포지션 |
| :--------------- | ----------- |
| **윤도현**(팀장) | 클라이언트  |
| 박준표           | 클라이언트  |
| 이상훈           | 클라이언트  |
| 김희제           | 클라이언트  |
| 서우린           | 서버        |
| 권용진           | 서버        |

---
