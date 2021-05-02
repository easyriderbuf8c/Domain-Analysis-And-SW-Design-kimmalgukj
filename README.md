# KickShare!

#### TEAM 김말국 : 김민창 안상희 용상호 황지훈

2020학년도 2학기 도메인분석및설계 과목에서 진행된 프로젝트입니다.

## 1. Motivation
보통 대학교 캠퍼스는 매우 넓고 대중교통도 원활하게 지원되고 있지 않다. 따라서 전동 킥보드 공유 서비스를 대학교에 적용시킴으로써 수업과 수업사이의 짧은 시간내에 넓은 캠퍼스를 보다 편하게 이동할 수 있을 것이며 학교 외부 인근 주변시설도 편하게 이용할 수 있을 것이다. 

## 2. Use Case Diagram
![uc다이어그램](https://user-images.githubusercontent.com/55920132/101247206-71755a80-375b-11eb-9c2d-57006b2ab59e.png)

## 3. Main Display
<img src="https://user-images.githubusercontent.com/75024316/102875787-a1c13680-4487-11eb-9ea8-7602cb826036.png"  width="160" height="280"><img src="https://user-images.githubusercontent.com/75024316/102875848-b6053380-4487-11eb-8d32-d61792be81be.png"  width="160" height="280"><img src="https://user-images.githubusercontent.com/75024316/102875873-bdc4d800-4487-11eb-84d9-3df4801913bc.png"  width="160" height="280"><img src="https://user-images.githubusercontent.com/75024316/102875855-b7cef700-4487-11eb-9479-a9e5b51223af.png"  width="160" height="280"><img src="https://user-images.githubusercontent.com/75024316/102876064-0da39f00-4488-11eb-9297-877a68a57ad5.png" width="160" height="280"><img src="https://user-images.githubusercontent.com/75024316/102875890-c5847c80-4487-11eb-892c-778e4efa653b.png" width="160" height="280"><img src="https://user-images.githubusercontent.com/75024316/102875952-dcc36a00-4487-11eb-98e5-ab87ef830236.png" width="160" height="280"><img src="https://user-images.githubusercontent.com/75024316/102875928-d2a16b80-4487-11eb-840f-acfc7a4bb2c1.png" width="160" height="280">


## 4. Implementation - UI Layer
### initial package
* MethodActivity.class : 서비스 사용 방법을 안내해준다.
* LoginActivity.class : 서비스 사용을 위해 로그인을 한다.
  * 관리자 모드 로그인은 01000000000로 한다.
  
## 4-1. Use Case 1 : Rent Kickboard / Use Case 3 : Charge Point / Use Case 5 : Calculate Fare
### main package
* MainActivity.class : 사용자가 이용할 서비스 메뉴를 선택할 수 있다.
### main의 rent package
* RentActivity.class : 포인트 확인 (PointActivity.class), 주변 킥보드 확인, QR Code 서비스 이용 가능
  * PointActivity.class : 사용자가 킥보드를 대여중이라면 화면에 대여 중이라는 표시와 함께 잔여 포인트와 이용 포인트가 나온다. 
    * 포인트 충전 버튼을 누르면 결제 모듈을 통해 포인트를 충전할 수 있다.
  * MapActivity.class : 사용자가 지도를 통해 킥보드 위치와 배터리를 확인할 수 있다.
  * QrActivity.class : 사용자가 카메라를 통해 QR Code를 인식시키면, 알림창에 '대여 완료!'라는 메시지와 함께 킥보드 대여를 시작한 시간이 나타난다.
  
## 4-2. Use Case 4 : Manage Kickboard
### admin package
* AdminActivity.class : 관리자가 이용할 메뉴를 선택할 수 있다.
  * Checkuser.class : 관리자가 서비스 이용 규정을 어긴 사용자에게 킥보드 반환을 요청하거나 킥보드 이용을 중지할 수 있다.
  * AdminMap.class : 관리자가 지도를 통해 킥보드 위치를 확인할 수 있다.
  * DistributeKickboard.class : 관리자가 킥보드 리스트를 보고 킥보드 매니저에게 분배를 요청할 수 있다. (주기적으로 킥보드 분배가 이루어지는 것을 실시간으로 보여줄 수 없어서 이렇게 구현함)
    * 분배 요청 버튼을 클릭하면, 분배가 완료되어 킥보드 리스트가 사라지게 된다.
    
## 5. Implementation - Domain Layer
### DBAccess package
* For DBAccess
  * AbstractAdapter, AbstractFactory, AdapterList, ExternalDBAdapter, InternalDBAdapter

### Distribution package
* For Manage Kickboard
  * DistributionPlanner, KickboardInfo, KickboardStation

### FareCalculation package
* For Fare Calculate
  * FareCalculator, FareStrategyFactory, OutsiderStrategy, SchoolStaffStrategy, StudentStrategy, TotalStrategy

## 6. Applied Pattern
### GRASP Pattern
* Creator, Controller, Low Coupling, High Cohesion, Polymorphism, Pure Fabrication, Indirection, Protected Variations

### GoF Pattern
* Adapter, Singleton, Composite, Facade, Observer, Factory, Strategy

### Architectural Layers pattern
### Micro architectural design patterns

## 7. 기타
* 개발 환경 : Android Studio, Java
* Compile SDK Version : 30 (API 30: Android 10.0+ (R))
* minSdkVersion : 24
* 지도 : Google Map API 이용

## 8. Reference

- 플라워로드 사이트, http://www.flowerroad.ai/
- 운전면허정보 검증 사이트, https://dlv.koroad.or.kr/
- 4+1 view 위키피디아, https://en.wikipedia.org/wiki/4%2B1_architectural_view_model  
- thick client vs thin client, https://simplicable.com/new/thin-client-vs-thick-client 
- 전송 계층 보안, 위키피디아, https://en.wikipedia.org/wiki/전송_계층_보안
- sequence diagram 구성 및 작성법, https://sswpgm.tistory.com/29
- 공유 킥보드 서비스 알파카, https://alpaca.kr/
