# 어웡 (Ueong)

```
 █████╗ ██████╗      ███╗   ███╗ █████╗ ██████╗ ██╗  ██╗███████╗████████╗
██╔══██╗██╔══██╗     ████╗ ████║██╔══██╗██╔══██╗██║ ██╔╝██╔════╝╚══██╔══╝
███████║██████╔╝     ██╔████╔██║███████║██████╔╝█████╔╝ █████╗     ██║   
██╔══██║██╔══██╗     ██║╚██╔╝██║██╔══██║██╔══██╗██╔═██╗ ██╔══╝     ██║   
██║  ██║██║  ██║     ██║ ╚═╝ ██║██║  ██║██║  ██║██║  ██╗███████╗   ██║   
╚═╝  ╚═╝╚═╝  ╚═╝     ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝   ╚═╝  
                        AR × 동네 중고거래 마켓플레이스
```

<div align="center">

![Swift](https://img.shields.io/badge/Swift-5.0-FA7343?logo=swift&logoColor=white)
![iOS](https://img.shields.io/badge/iOS-17.5+-000000?logo=apple&logoColor=white)
![SwiftUI](https://img.shields.io/badge/SwiftUI-5-0070C9?logo=swift&logoColor=white)
![RealityKit](https://img.shields.io/badge/RealityKit-ObjectCapture-5856D6?logo=apple&logoColor=white)
![Socket.IO](https://img.shields.io/badge/Socket.IO-Realtime_Chat-010101?logo=socketdotio&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-EC2-FF9900?logo=amazonwebservices&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=nodedotjs&logoColor=white)

</div>

---

## 한 줄 소개

> **LiDAR로 상품을 3D 스캔하고, 구매자는 실제 공간에 AR로 배치해 확인하는 동네 중고거래 마켓플레이스**

---

## 주요 기능

### AR 3D 스캔 — 판매자

LiDAR 카메라로 판매할 물건을 3방향(Orbit)으로 촬영하면, on-device 포토그래메트리로 자동으로 USDZ 3D 모델을 생성합니다.

| 스캔 시작 | 3-Orbit 촬영 가이드 | 3D 재구성 진행 |
|:---------:|:-------------------:|:--------------:|
| ![스크린샷](./docs/images/ar_scan_start.png) | ![스크린샷](./docs/images/ar_orbit_guide.png) | ![스크린샷](./docs/images/ar_reconstruct.png) |

### AR 뷰어 — 구매자

상품 상세 페이지에서 AR 버튼을 누르면, 실제 방 안에 3D 모델을 배치해 크기와 디자인을 확인할 수 있습니다.

| 상품 상세 | AR 뷰어 (실제 공간 배치) |
|:---------:|:------------------------:|
| ![스크린샷](./docs/images/post_detail.png) | ![스크린샷](./docs/images/ar_viewer.png) |

### 마켓플레이스

| 상품 목록 (동네/AR 필터) | 게시글 등록 | 실시간 채팅 |
|:------------------------:|:-----------:|:-----------:|
| ![스크린샷](./docs/images/posts_list.png) | ![스크린샷](./docs/images/write_post.png) | ![스크린샷](./docs/images/chat.png) |

**구현된 기능:**

- 상품 CRUD (등록 / 수정 / 비활성화)
- 동네·AR 전용·정렬 기준 필터 + 검색어 검색
- 상품 사진 다중 업로드 (PHPickerViewController → multipart)
- 관심 목록 (낙관적 업데이트)
- 거래 희망 장소 지도 핀 선택 (MapKit)
- 판매 내역 (거래대기 / 거래완료)
- Socket.IO 기반 1:1 실시간 채팅
- JWT 자동 로그인 + iOS Keychain 토큰 저장

---

## 기술 스택

### iOS / Frontend

| 분류 | 기술 |
|------|------|
| **UI** | ![SwiftUI](https://img.shields.io/badge/SwiftUI-선언형_UI-0070C9?logo=swift&logoColor=white) ![UIKit](https://img.shields.io/badge/UIKit-브리징-2396F3?logo=apple&logoColor=white) |
| **아키텍처** | ![MVVM](https://img.shields.io/badge/MVVM-Repository_Pattern-6C6C6C) ![Combine](https://img.shields.io/badge/Combine-@Published-FA7343?logo=swift&logoColor=white) |
| **AR / 3D** | ![RealityKit](https://img.shields.io/badge/RealityKit-ObjectCaptureSession-5856D6?logo=apple&logoColor=white) ![ARKit](https://img.shields.io/badge/ARKit-QuickLook-5856D6?logo=apple&logoColor=white) |
| **지도** | ![MapKit](https://img.shields.io/badge/MapKit-거래_장소_선택-34C759?logo=apple&logoColor=white) |
| **보안** | ![Keychain](https://img.shields.io/badge/Keychain-JWT_저장-000000?logo=apple&logoColor=white) |
| **미디어** | ![PhotosUI](https://img.shields.io/badge/PhotosUI-PHPickerViewController-4CAF50) ![AVKit](https://img.shields.io/badge/AVKit-튜토리얼_영상-FF3B30) |

### 네트워크

| 분류 | 기술 |
|------|------|
| **REST API** | ![URLSession](https://img.shields.io/badge/URLSession-async%2Fawait-FA7343?logo=swift&logoColor=white) — Alamofire 미사용, 제네릭 직접 구현 |
| **실시간** | ![Socket.IO](https://img.shields.io/badge/socket.io--client--swift-SPM-010101?logo=socketdotio&logoColor=white) + ![Starscream](https://img.shields.io/badge/Starscream-4.0.8-4B8BBE) |
| **인증** | ![JWT](https://img.shields.io/badge/JWT-Bearer_Token-000000?logo=jsonwebtokens&logoColor=white) (커스텀 서버 발급) |

### 인프라 / 백엔드

| 분류 | 기술 |
|------|------|
| **서버** | ![AWS EC2](https://img.shields.io/badge/AWS-EC2-FF9900?logo=amazonwebservices&logoColor=white) 단일 인스턴스 |
| **API** | ![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=nodedotjs&logoColor=white) — REST API + Socket.IO 서버 |
| **파일 저장** | EC2 로컬 디스크 (이미지 + USDZ, `express.static` 서빙) |
| **의존성 관리** | ![SPM](https://img.shields.io/badge/SPM-Swift_Package_Manager-FA7343?logo=swift&logoColor=white) |

---

## 시스템 아키텍처

### 전체 구조

```
┌─────────────────────────────────────────────────────────────────┐
│                      iOS 앱 (어웡)                               │
│                                                                 │
│  ┌─────────────┐    ┌─────────────┐    ┌──────────────────────┐│
│  │ SwiftUI View│───►│  ViewModel  │───►│    Repository (×11)  ││
│  │  (15개 화면) │    │ @Published  │    │ Post / Photo / AR    ││
│  └─────────────┘    └─────────────┘    │ User / Chat / ...    ││
│                            │           └──────────┬───────────┘│
│                     NotificationCenter            │             │
│                            │           ┌──────────▼───────────┐│
│  ┌─────────────────────┐   │           │  Network/APICall.swift││
│  │ SocketManagerService│   │           │  제네릭 HTTP 클라이언트 ││
│  │ (Socket.IO Singleton)│  │           │  URLSession async/await│
│  └─────────────────────┘   │           └──────────────────────┘│
└──────────────┬─────────────┼──────────────────────┬────────────┘
               │ Socket.IO   │ NotificationCenter    │ HTTP
               │ WebSocket   │ .tokenExpired 등      │ REST API
               ▼             ▼                       ▼
┌─────────────────────────────────────────────────────────────────┐
│                  AWS EC2 (Node.js + Express)                     │
│                                                                 │
│   REST API (JSON)  ─────────────────────────────────────────    │
│   Socket.IO 채팅 서버  ──────────────────────────────────────   │
│   express.static (이미지 + USDZ 파일 서빙)  ────────────────── │
└─────────────────────────────────────────────────────────────────┘
```

### 앱 내부 레이어 구조 (MVVM + Repository)

```
┌──────────────────────────────────────────────────────────────┐
│  Presentation Layer                                          │
│                                                              │
│  UI/Screens/<화면>View.swift  ←──►  <화면>ViewModel.swift    │
│  UI/Component/ (PostRow, SearchBar, SelectRegion ...)        │
│  ARCapture/  (독립 서브시스템 — 상태 머신 구조)              │
├──────────────────────────────────────────────────────────────┤
│  Domain Layer                                                │
│                                                              │
│  Models/  (Post, User, Chat, AR, Emd, Message ...)          │
│  System/AppState.swift  (전역 인증 상태, EnvironmentObject)  │
├──────────────────────────────────────────────────────────────┤
│  Data Layer                                                  │
│                                                              │
│  Repositories/ (11개 — 도메인별 API 추상화)                   │
│  Network/APICall.swift  (Singleton, 300줄)                    │
│  Service/Socket.swift   (SocketManagerService Singleton)      │
│  Utils/  (KeychainHelper · TokenManager · UserDefaultsManager)│
└──────────────────────────────────────────────────────────────┘
```

### 데이터 흐름

```
사용자 액션 → SwiftUI View
       │
       ▼  Task { await ... }
   ViewModel  (@Published 상태 소유)
       │  try await repository.method()
       ▼
   Repository  (도메인 API 추상화)
       │  try await APICall.shared.get/post/patch/delete()
       ▼
   APICall.request<T: Decodable>()
       │  URL 구성 → Bearer JWT 헤더 → URLSession.data(for:)
       ▼
   JSONDecoder().decode(T.self, from: data)
       │
       ▼  await MainActor.run { self.data = result }
   @Published 변경 → SwiftUI 자동 재렌더링

── 실시간 채팅 ──────────────────────────────────────────
   ChatView → socket.emit("sendMessage", ...)
       │
       ▼  Socket.IO 서버 → "sendMessageResponse"
   SocketManagerService → NotificationCenter.post(.sendMessageResponse)
       │
       ▼  ChatViewModel (Observer)
   @Published var messages → SwiftUI 재렌더링
```

---

## AR 기능 상세

### 두 가지 AR 워크플로우

어웡의 AR은 완전히 다른 목적의 두 워크플로우로 구성됩니다.

| 워크플로우 | 사용자 | 핵심 API | 담당 모듈 |
|-----------|--------|---------|---------|
| **3D 스캔** | 판매자 — 상품을 3D 모델로 변환 | `ObjectCaptureSession` + `PhotogrammetrySession` | `ARCapture/` (26개 파일) |
| **AR 뷰어** | 구매자 — 실제 공간에 3D 모델 배치 | `QLPreviewController` (AR Quick Look) | `UI/Screens/AugmentedReality/` |

### AR 스캔 파이프라인

```
[WritePost] → "모델 생성하기" → MainCaptureView
                                      │
          ┌───────────────────────────▼──────────────────────────────┐
          │ ObjectCaptureSession (RealityKit)                         │
          │                                                           │
          │  Configuration {                                          │
          │    checkpointDirectory: 재구성 재개용 스냅샷 저장           │
          │    isOverCaptureEnabled: true  // 추가 촬영 허용           │
          │  }                                                        │
          │                                                           │
          │  CapturePrimaryView                                       │
          │    ├── ObjectCaptureView  (바운딩 박스 + 카메라 피드)      │
          │    ├── CaptureOverlayView (촬영 수, 수동 셔터, 품질 피드백) │
          │    └── 3-Orbit 가이드     (수평 × 저각 × 고각 3방향)      │
          │         └── TutorialVideoView (iPhone/iPad별 MP4 × 10개) │
          └───────────────────────────┬──────────────────────────────┘
                     session.finish() │
                                      ▼  objectCaptureSession = nil (GPU 해제)
          ┌───────────────────────────▼──────────────────────────────┐
          │ PhotogrammetrySession (on-device 포토그래메트리)           │
          │                                                           │
          │  HEIC 이미지 폴더 → .modelFile(url: outputFile) 요청      │
          │                                                           │
          │  for await output in UntilProcessingCompleteFilter(...) { │
          │    .requestProgress      → 진행률 UI (0% ~ 100%)          │
          │    .requestProgressInfo  → 처리 단계 표시                  │
          │      preProcessing → imageAlignment → pointCloudGen       │
          │      → meshGeneration → textureMapping → optimization     │
          │    .processingComplete   → USDZ 완성                      │
          │  }                                                        │
          └───────────────────────────┬──────────────────────────────┘
                                      │
                         Documents/Models/3D_<UUID>.usdz 저장
                                      │
                                      ▼
                          QLPreviewController (AR Quick Look)
                          스캔 직후 AR 미리보기 → WritePost 복귀
```

### AR 뷰어 파이프라인

```
[PostDetail] → post.ar_model_id != nil → "AR로 보기" 버튼 활성화
                                                │
                                                ▼
                              ArView(url: post.ar_model_directory)
                                                │
                              URLSession.dataTask(서버 USDZ 다운로드)
                                                │
                                                ▼
                              QLPreviewController (AR Quick Look)

                              Apple이 자동 처리:
                                ✓ 바닥/테이블 평면 자동 감지
                                ✓ 핀치 제스처로 크기 조절
                                ✓ 드래그로 위치 이동
                                ✓ 환경 조명(IBL) + 그림자 자동 적용
```

### Swift Concurrency 활용 포인트

`ObjectCaptureSession`의 이벤트를 콜백 없이 `AsyncSequence`로 구독합니다.

```swift
// 실시간 피드백 구독 — for await 루프
for await newFeedback in session.feedbackUpdates {
    updateFeedbackMessages(for: newFeedback)
}

// 세션 상태 변경 구독
for await newState in session.stateUpdates {
    onStateChanged(newState: newState)  // 자동 상태 전환
}
```

`PhotogrammetrySession.outputs`가 완료 후에도 스트림을 닫지 않는 문제는 커스텀 `AsyncIteratorProtocol`로 해결했습니다.

```swift
struct UntilProcessingCompleteFilter<Base>: AsyncSequence, AsyncIteratorProtocol {
    mutating func next() async -> Element? {
        if completed { return nil }  // processingComplete 이후 자동 종료
        // ...
    }
}
```

### AR ↔ 마켓플레이스 연결 구조

두 도메인은 `Post` 모델의 두 Optional 필드로 느슨하게 연결됩니다.

```swift
struct Post: Identifiable, Decodable {
    // ...
    var ar_model_id: Int?           // AR 연결 여부 판별 키
    var ar_model_directory: String? // USDZ 파일 경로 (서버 상대 경로)
}

// PostDetail — AR 버튼 분기
if post.ar_model_id == nil {
    // "등록된 AR 모델이 없습니다." 알림
} else {
    NavigationLink → ArView(url: post.ar_model_directory)
}
```

AR 모델이 없는 일반 게시글도 완전히 지원하면서, `ar_model_id`가 있을 때만 AR 기능을 활성화합니다.

---

## 설치 및 실행 방법

### 요구 사항

| 항목 | 최소 요구 사항 |
|------|-------------|
| **Xcode** | 15.0 이상 |
| **iOS** | 17.5 이상 |
| **기기 (AR 스캔)** | LiDAR 탑재 기기 필수 (iPhone 12 Pro 이상) |
| **기기 (AR 뷰어)** | iPhone / iPad 전 모델 지원 |

> AR 스캔 기능(`ObjectCaptureSession`)은 **LiDAR 탑재 기기**에서만 동작합니다.  
> AR 뷰어(`QLPreviewController`)는 LiDAR 없이도 모든 기기에서 사용 가능합니다.

### 실행 순서

```bash
# 1. 저장소 클론
git clone https://github.com/<your-username>/ar-marketplace-ios.git
cd ar-marketplace-ios

# 2. Xcode로 프로젝트 열기
open MVVM_Ueong.xcodeproj
```

```
# 3. Xcode 내 설정
- Signing & Capabilities → 개인 Team ID로 변경
- 실기기 선택 (시뮬레이터에서 AR 기능 미지원)

# 4. Run (⌘R)
```

> **서버 연동**: 현재 `Constants.swift`의 `baseURL`이 개발 서버를 가리킵니다.  
> 로컬 서버 실행이 필요한 경우 Node.js 백엔드 저장소를 별도로 클론해 실행하세요.

### 프로젝트 구조

```
ar-marketplace-ios/
├── MVVM_Ueong/
│   ├── ARCapture/          # AR 스캔 · 재구성 서브시스템 (26개 파일)
│   │   ├── AppDataModel.swift          # 핵심 상태 머신 (394줄)
│   │   ├── CaptureFolderManager.swift  # 파일시스템 관리 (294줄)
│   │   ├── ReconstructionPrimaryView.swift
│   │   └── Resources/      # 튜토리얼 MP4 × 10개 (iPhone/iPad)
│   ├── Models/             # Codable 도메인 구조체 (10개)
│   ├── Network/            # APICall.swift — HTTP 공통 클라이언트
│   ├── Repositories/       # 도메인별 API 추상화 (11개)
│   ├── Service/            # Socket.IO 서비스
│   ├── System/             # AppDelegate, AppState
│   ├── UI/
│   │   ├── Component/      # 재사용 컴포넌트 (PostRow, SearchBar ...)
│   │   └── Screens/        # 화면 15개 × (View + ViewModel)
│   └── Utils/              # Keychain, TokenManager, Formatter ...
└── docs/
    ├── analysis/           # 단계별 기술 분석 문서
    └── presentation.pdf    # 발표자료
```

---

## 발표자료

[📄 프로젝트 발표 슬라이드](./docs/presentation.pdf)

---

## 팀원 소개

| 역할 | 담당 |
|------|------|
| **iOS 앱 개발** | SwiftUI · MVVM+Repository · AR 스캔/뷰어 · 마켓플레이스 전 기능 |
| **Cloud / 백엔드** | Node.js/Express API · Socket.IO · AWS EC2 인프라 · 파일 서버 |

<table>
  <tr>
    <td align="center">
      <b>iOS 담당</b><br/>
      <sub>SwiftUI · RealityKit · Socket.IO</sub>
    </td>
    <td align="center">
      <b>Cloud 담당</b><br/>
      <sub>Node.js · Express · AWS EC2</sub>
    </td>
  </tr>
</table>

---

<div align="center">

**Swift 5.0** · **iOS 17.5+** · **RealityKit** · **SwiftUI** · **Socket.IO** · **AWS EC2**

*109 Swift files · ~11,040 lines · 15 screens · 11 repositories · ~30 API endpoints*

</div>
