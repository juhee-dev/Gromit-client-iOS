# 🐣 Gromit — 깃허브 커밋으로 키우는 나만의 다마고치

> **Grow + Commit = Gromit** </br>
> 깃허브 커밋을 먹이 삼아 캐릭터를 성장시키고, 같은 목표를 가진 사람들과 함께 챌린지를 통해 개발 습관을 만들어가는 iOS 앱

<p align="center">
  <a href="https://apps.apple.com/kr/app/%EA%B7%B8%EB%A1%9C%EB%B0%8B/id6451416113" tabIndex="0">
    <img class="bn46" src="https://developer.apple.com/assets/elements/badges/download-on-the-app-store.svg" alt="bn45"/>
  </a>
</p>


<br>

## 📌 프로젝트 소개

개발자라면 누구나 공감하는 **"깃허브 잔디 관리"**. 꾸준히 커밋하고 싶지만 동기 부여가 쉽지 않죠.

Gromit은 하루하루의 커밋을 캐릭터의 먹이로 전환해 **성취감**을 만들고, 챌린지 기능으로 **같은 목표를 가진 사람들과 함께** 습관을 형성할 수 있도록 돕는 서비스입니다.

- **UMC(University MakeUs Challenge) 3rd** 에서 기획·개발된 프로젝트
- 팀 구성: iOS 3, 백엔드 3, 기획/디자인 1 (총 7인)
- 역할: iOS Developer
- 기간: 2023.01 - 2023.11 (약 10개월)
- 주요 기술: SwiftUI, MVVM, Alamofire

<br>

## 📱 주요 기능
<img width="500" alt="image" src="https://github.com/user-attachments/assets/6cf6af6d-e639-4aa8-a005-b9d4a3852dba">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/2b02ea0d-82ee-4443-b51d-fbedaa4fd234">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/02beff07-c3b8-41f4-8372-81cf64d81623">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/e36ce852-eab3-44c2-81c2-b9841d62e038">

<br><br>

## 📸 스크린샷
| **메인 홈** | **홈 최종진화** | **컬렉션** |
| :---: | :---: | :---: |
| <img width="230" alt="Image" src="https://github.com/user-attachments/assets/554f1b1f-21aa-47e4-ab9a-4090e67090ee" /> | <img width="230" alt="Image" src="https://github.com/user-attachments/assets/3b7a5a56-b62e-46af-b234-66eba80d2866" /> | <img width="230" alt="Image" src="https://github.com/user-attachments/assets/d1303998-c669-419a-9dcd-b31cf42762cf" />
| **참여 중 챌린지** | **챌린지 생성** | **설정** |
| <img width="230" alt="Image" src="https://github.com/user-attachments/assets/3278e0db-2a98-460a-9027-00a09b15dec2" /> | <img width="230" alt="Image" src="https://github.com/user-attachments/assets/f1dce55a-0560-468e-90b3-bfb8273ba268" /> | <img width="230"  alt="Image" src="https://github.com/user-attachments/assets/74a457a1-f46e-4d2e-94e3-f6b75c0ab75f" />
| **닉네임 변경** | **개발자 도구 45위** |
| <img width="230" alt="Image" src="https://github.com/user-attachments/assets/89c2ce74-5698-4f41-8467-71c4d1c04abd" /> | <img width="230" alt="Image" src="https://github.com/user-attachments/assets/7efdd58e-f8ca-4a4a-b6d0-e99cfd30567f" />

<br><br>

## 🙋 기여한 부분
- 전체 UI의 약 65% 구현
  <details>
    <summary>자세한 내용</summary>
    온보딩, 홈(캐릭터 육성), 챌린지 생성·목록·상세·참여, 설정 화면을 SwiftUI로 직접 설계하고 구현했습니다. 캐릭터 경험치와 챌린지 참여 현황을 보여주는 Progress Bar는 GeometryReader로 컨테이너 너비를 런타임에 측정해 달성률을 동적으로 표현했습니다.
  </details>
- Alamofire 기반 커스텀 네트워크 레이어 설계 전체 & 전체 API의 약 50% 연동
    <details>
    <summary>자세한 내용</summary>
    처음에는 더 높은 추상화 수준을 기대하고 Moya를 도입했지만, 실제로 적용해보니 프로젝트 규모에 비해 보일러플레이트 코드가 늘어나 오히려 복잡도가 높아졌습니다. 이를 인식하고 Alamofire를 직접 감싼 커스텀 NetworkingClient 래퍼 클래스로 전환했습니다. URL 관리(ServiceURL enum), 타임아웃 설정, JSON 디코딩을 내부에서 일괄 처리하도록 설계해 각 ViewModel에서는 `NetworkingClient.shared.request(...)`만 호출하면 되는 구조를 마련했습니다. 덕분에 팀원들이 통신 로직을 신경 쓰지 않고 비즈니스 로직에만 집중할 수 있었습니다.
  </details>
- Combine을 활용한 MVVM 패턴 구현
  <details>
    <summary>자세한 내용</summary>
    `@Published` + `onReceive` 패턴으로 ViewModel의 API 응답을 View에 전달하는 구조를 구현했습니다. API 결과를 OutputEvent enum으로 분리해 성공·실패·에러 케이스를 명확히 정의함으로써, View는 비즈니스 로직을 전혀 모르는 상태에서 이벤트만 받아 팝업과 화면 전환을 처리하도록 관심사를 분리했습니다.
  </details>

<br><br>

## 📝 성과 & 회고
### 성과
- 출시 첫 주에 앱스토어 개발자 도구 카테고리 45위를 달성했습니다.
### 회고
첫 iOS 프로젝트로서 기획부터 출시까지 전 과정을 경험했지만, 돌아보면 아쉬운 점도 있습니다.<br>
- 액세스 토큰을 AppDataService에 저장했는데, 보안상 민감한 정보는 Keychain에 저장해야 한다는 것을 이후에 알게 됐습니다.<br>
- NetworkingClient 내부의 모든 API 요청 후에 `sleep(1)`로 인위적인 딜레이를 적용한 것도 아쉬운 부분입니다. 타이밍 이슈를 임시방편으로 막은 것인데, 비동기 처리 흐름을 제대로 이해했다면 적절한 completion 시점에 UI를 업데이트하는 방식으로 해결했을 것입니다.<br>
- Combine의 `@Published` + `onReceive` 패턴을 일부 화면에만 적용하고 나머지는 미완성으로 남겨, 코드베이스 전체에 일관된 데이터 흐름을 유지하지 못한 점도 아쉽습니다. 초기 설계 단계에서 팀 전체가 데이터 흐름 방식을 통일하는 것이 얼마나 중요한지 배웠습니다.<br>

이 프로젝트를 통해 단순히 기능을 동작시키는 것과 유지보수 가능한 구조로 설계하는 것이 다르다는 점을 직접 체감하였고, 아쉬웠던 점을 보완하여 On My Way 프로젝트를 진행하였습니다.
