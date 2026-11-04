# Perfect Chair — App Store 제출 작업지시서

이 문서 하나로 **처음부터 심사 제출까지** 끝나도록 썼습니다.
위에서 아래로 순서대로 따라가시면 됩니다. 되돌아갈 일은 없습니다.

- 앱 이름: **Perfect Chair** (한국어 표기 「퍼펙트 체어」)
- Bundle ID: **`com.perfectchair.perfectChair`**
- 버전 / 빌드: **1.0.0 (1)**
- 팀: **AJUVV9A2NC** (hyeyoung lee)
- 최소 iOS: **14.0** · iPhone + iPad 모두 지원
- 작성일: 2026-11-04

---

## 0. 준비물 체크리스트

작업 시작 전에 아래 다섯 개가 손에 있어야 합니다.

| # | 준비물 | 어디에 있나 |
|---|---|---|
| 1 | 서명된 IPA 파일 | https://github.com/milovane777/perfect-chair-store/releases/tag/v1.0.0-build1 (27 MB) |
| 2 | 스크린샷 | https://github.com/milovane777/perfect-chair-store → `screenshots/` — iPhone 6.9형, iPhone 6.3형, iPad 13형 |
| 3 | 10개 언어 메타데이터 | 같은 저장소 `metadata/<로케일>/` — 복사·붙여넣기용 텍스트 파일 |
| 4 | 개인정보 처리방침 URL | `https://milovane777.github.io/perfect-chair-privacy/` |
| 5 | 고객 지원 URL | `https://milovane777.github.io/perfect-chair-privacy/support.html` |

> 두 URL은 **지금 살아 있습니다.** 브라우저에 붙여 넣어 열리는지 한 번만 확인하고 시작하세요.
> 열리지 않으면 그 자리에서 멈추고 담당자에게 알려 주십시오. 죽은 URL은 **확실한 반려 사유**입니다.

---

## 1. App Store Connect에 앱 레코드 만들기

[appstoreconnect.apple.com](https://appstoreconnect.apple.com) → **나의 앱** → 왼쪽 위 **＋** → **신규 앱**.

입력값은 아래 표 그대로입니다. **기본 언어를 반드시 English (U.S.)로 두십시오.**

| 칸 | 입력값 | 주의 |
|---|---|---|
| 플랫폼 | **iOS** 체크 | |
| 이름 | `Perfect Chair` | 전 세계에서 유일해야 합니다. 이미 쓰이고 있다면 **§1-1**로 |
| 기본 언어 | **English (U.S.)** | ⚠️ **한 번 정하면 바꿀 수 없습니다.** 가장 흔한 실수입니다 |
| 번들 ID | `com.perfectchair.perfectChair` | 목록에 없으면 **§1-2**로 |
| SKU | `perfect-chair-ios-001` | 내부 식별용. 아무 값이나 가능하지만 이 값으로 통일 |
| 사용자 액세스 | 전체 액세스 | |

### 1-1. 이름이 이미 쓰이고 있을 때

아래 순서로 시도하고, **처음 통과한 것**을 씁니다. 통과한 이름을 담당자에게 알려 주세요.

1. `Perfect Chair`
2. `Perfect Chair: Salon Notes` (26자)
3. `Perfect Chair Salon` (19자)

이름을 바꿔 쓰게 되면 **§7의 각 언어 `name.txt`도 같은 이름으로 맞춰야 합니다**(한국어 「퍼펙트 체어」는 그대로 두셔도 됩니다).

### 1-2. 번들 ID가 목록에 없을 때

[developer.apple.com](https://developer.apple.com/account/resources/identifiers/list) → **Identifiers** → **＋** → App IDs → App →
Description `Perfect Chair`, Bundle ID는 **Explicit**으로 `com.perfectchair.perfectChair`.
Capabilities는 **아무것도 켜지 마십시오** — 이 앱은 푸시도, iCloud도, 로그인도 쓰지 않습니다.
등록 후 App Store Connect를 새로고침하면 목록에 나타납니다.

---

## 2. 빌드 업로드

가장 쉬운 방법은 **Transporter**(Mac App Store 무료)입니다.

1. Transporter 실행 → Apple ID로 로그인
2. `Perfect Chair.ipa`를 창에 끌어다 놓기
3. **전송(Deliver)** 클릭
4. "전송 완료" 표시를 확인

업로드 후 App Store Connect의 **TestFlight** 탭에 빌드가 나타나기까지 **5~30분**이 걸립니다.
상태가 "처리 중"에서 바뀌어야 다음으로 갑니다. 기다리는 동안 §3~§8을 먼저 채워 두세요.

> **암호화 관련 질문이 뜨면:** 이 앱은 `ITSAppUsesNonExemptEncryption = false`가 이미 Info.plist에 들어 있어
> 질문이 뜨지 않는 것이 정상입니다. 혹시 뜬다면 **"아니요"**를 고르십시오. 네트워크 기능 자체가 없습니다.

업로드가 거부되면 **§11 문제 해결**을 보십시오.

---

## 3. 앱 정보 (General → App Information)

| 칸 | 입력값 |
|---|---|
| 기본 언어 | English (U.S.) — §1에서 정한 값, 수정 불가 |
| 번들 ID | `com.perfectchair.perfectChair` |
| 기본 카테고리 | **Business** |
| 보조 카테고리 | **Productivity** |
| 콘텐츠 권한 | "이 앱에 제3자 콘텐츠가 포함되어 있습니까?" → **아니요** |

### 연령 등급 (Age Rating → 편집)

모든 항목에 **"없음(None)"**을 고르십시오. 결과는 **4+** 가 나와야 합니다.
아래 세 개만 특별히 주의해서 고르세요.

- 무제한 웹 접근(Unrestricted Web Access) → **아니요** (브라우저 기능 없음)
- 도박 → **아니요**
- 의료/치료 정보(Medical/Treatment Information) → **아니요**
  → 이 앱은 모발·두피 메모를 **사용자가 직접 적는 기록장**이지, 의학적 조언을 제공하지 않습니다.

---

## 4. 가격 및 배포 (Pricing and Availability)

| 칸 | 입력값 |
|---|---|
| 가격 | **무료 (Free, Tier 0)** |
| 배포 국가 | **모든 국가 및 지역** |
| App Store 배포 | 켬 |

---

## 5. 앱 개인정보 (App Privacy) — ★ 가장 중요

왼쪽 메뉴 **앱 개인정보** → **시작하기**.

> **"이 앱에서 데이터를 수집합니까?" → `아니요(No)`를 고르십시오.**

이것이 정확한 답입니다. 추측이 아닙니다. 근거:

- Android 쪽에서는 `INTERNET` 권한 자체를 제거했고, iOS 빌드에도 네트워크 코드가 없습니다
- 분석·광고·크래시 리포트 SDK가 하나도 들어 있지 않습니다
- 계정도, 서버도 없습니다

"아니요"를 고르면 상세 항목 입력 화면이 **나오지 않습니다.** 그게 정상입니다.

| 칸 | 입력값 |
|---|---|
| 개인정보 처리방침 URL | `https://milovane777.github.io/perfect-chair-privacy/` |

---

## 6. 스크린샷 올리기

`store/screenshots/` 안에 세 폴더가 있습니다. **폴더 이름이 곧 업로드할 칸 이름**입니다.

| 폴더 | App Store Connect 칸 | 해상도 | 필수? |
|---|---|---|---|
| `iphone-6.9/` | iPhone 6.9형 디스플레이 | 1320 × 2868 | ✅ 필수 |
| `iphone-6.3/` | iPhone 6.3형 디스플레이 | 1206 × 2622 | 칸이 보이면 채우기 |
| `ipad-13/` | iPad 13형 디스플레이 | 2064 × 2752 | ✅ 필수 (iPad 지원 앱) |

각 폴더에 **네 장**이 들어 있습니다.

| 파일 | 화면 |
|---|---|
| `01-clients.png` | 손님 목록 |
| `02-recipes.png` | 저장된 배합 |
| `03-calendar.png` | 시술 달력 |
| `04-tools.png` | 도구 (순서도·목표판·환산기) |

세 폴더 모두 **알파 채널 없는 불투명 PNG**이고 해상도를 검사해 두었습니다.
알파가 있으면 업로드가 거부되는데, 그 지점은 이미 처리했습니다.

**올리는 방법:** 각 칸에 해당 폴더의 PNG를 **파일 이름 순서(01 → 04) 그대로** 끌어다 놓으십시오.
순서가 App Store에 보이는 순서입니다.

**주의할 점**

- App Store Connect는 iPhone 칸 중 **가장 큰 것 하나만** 요구하고 나머지를 자동으로 줄여 씁니다.
  그래서 6.9형과 6.3형 중 **보이는 칸만** 채우면 됩니다. 둘 다 보이면 둘 다 채우십시오 — 파일은 준비돼 있습니다.
- 스크린샷은 **언어마다 따로** 올릴 수 있지만, **영어(기본 언어) 한 벌만 올리면 나머지 언어가 그것을 물려받습니다.**
  10개 언어에 전부 올리실 필요 **없습니다.** 영어 칸에만 올리십시오.
- 이미 올라간 스크린샷을 지우려면 사진 위에 마우스를 올리고 **×**를 누릅니다.

---

## 7. 10개 언어 메타데이터 넣기

### 언어를 추가하는 법

버전 페이지 오른쪽 위 **「한국어 ▾」 모양의 언어 선택기** → **「언어 추가」** → 아래 표의 언어를 고릅니다.
언어를 추가하면 그 언어 전용 입력 칸이 생깁니다.

### 넣을 순서와 목록

**영어가 기본 언어(1번)이고, 나머지는 미용 인구가 많은 시장 순서입니다.**
위에서부터 채우십시오. 중간에 시간이 끊겨도 위쪽이 더 중요한 시장입니다.

| 순 | App Store Connect에서 고를 이름 | 폴더 | 왜 이 순서인가 |
|---|---|---|---|
| 1 | **English (U.S.)** ★기본 | `en-US/` | 기본 언어. 번역이 없는 모든 지역이 이것을 봅니다 |
| 2 | **Chinese (Simplified)** | `zh-Hans/` | 중국·싱가포르. 단일 언어 기준 최대 미용 인구 |
| 3 | **Hindi** | `hi/` | 인도. 세계 2위 인구, 미용실 종사자 수 최상위권 |
| 4 | **Spanish (Spain)** | `es-ES/` | 중남미 전역 + 스페인. 20여 개국 공용 |
| 5 | **Arabic** | `ar-SA/` | 중동·북아프리카 22개국. 미용 지출 비중이 매우 높음 |
| 6 | **Portuguese (Brazil)** | `pt-BR/` | 브라질. 세계 2~3위 규모의 미용 시장 |
| 7 | **Russian** | `ru/` | 러시아·중앙아시아 |
| 8 | **Japanese** | `ja/` | 일본. 1인당 미용실 밀도 세계 최고 수준 |
| 9 | **Korean** | `ko/` | 한국. 개발자의 모국 시장 |
| 10 | **French (France)** | `fr-FR/` | 프랑스·벨기에·스위스·서아프리카 |

> Spanish는 `Spanish (Spain)`을 고르십시오. `Spanish (Mexico)`가 따로 있지만 하나만 넣으면 충분합니다.
> Chinese는 반드시 **Simplified**입니다. 앱이 담고 있는 번역이 간체입니다.

### 각 언어에서 채울 칸

폴더 안 파일 이름이 곧 칸 이름입니다. **파일을 열어 전체 복사 → 해당 칸에 붙여넣기.**

| 파일 | App Store Connect 칸 | 글자 수 제한 |
|---|---|---|
| `name.txt` | 이름 (Name) | 30 |
| `subtitle.txt` | 부제 (Subtitle) | 30 |
| `promotional_text.txt` | 프로모션 텍스트 | 170 |
| `keywords.txt` | 키워드 | 100 |
| `description.txt` | 설명 (Description) | 4000 |
| `release_notes.txt` | 이 버전의 새로운 기능 | — |

**모든 파일이 제한 안에 들어가도록 이미 검사했습니다.** 길이 때문에 잘릴 일은 없습니다.

### 언어와 무관하게 모든 언어에 똑같이 넣는 칸

| 칸 | 값 |
|---|---|
| 지원 URL (Support URL) | `https://milovane777.github.io/perfect-chair-privacy/support.html` |
| 마케팅 URL | **비워 두십시오** (없어도 됩니다) |
| 저작권 (Copyright) | `2026 hyeyoung lee` |

---

## 8. 빌드 선택

§2에서 올린 빌드가 처리되면, 버전 페이지의 **「빌드」** 항목에 **＋** 또는 **「빌드 추가」**가 생깁니다.
**1.0.0 (1)**을 고르십시오. 목록에 없으면 아직 처리 중입니다 — 기다렸다가 새로고침하십시오.

---

## 9. 심사 정보 (App Review Information)

| 칸 | 입력값 |
|---|---|
| 로그인 필요 | **체크 해제** (계정 기능이 없습니다) |
| 연락처 — 성 (First Name 칸 왼쪽) | `lee` |
| 연락처 — 이름 (오른쪽 칸) | `hyeyoung` |
| 연락처 — 전화번호 | `+821047434164` |
| 연락처 — 이메일 | `milovane7777@gmail.com` |
| 첨부 파일 | 없음 |

### 메모(Notes) 칸에 아래를 그대로 붙여넣으십시오

```
Perfect Chair is a fully offline notebook for hairdressers.

• No account and no sign-in. Nothing is gated — every feature is available
  immediately on first launch.
• The app has no network code at all. On Android the INTERNET permission is
  explicitly removed from the manifest; the iOS build contains no networking.
  This is why App Privacy is declared as "no data collected".
• Camera and photo library are used only when the user attaches a before/after
  photo to a service record. The image is copied into the app's private
  container. The photo library is never scanned or indexed.
• Notifications are local only (flutter_local_notifications). They ring a
  processing timer the user started. Nothing is scheduled remotely.
• Backup/restore writes and reads a file at a location the user picks through
  the system file picker.

How to see the main features quickly:
1. Clients tab → "Add client" → enter any nickname → Save.
2. Open that client → "New record" → fill in a formula, tap the timer.
3. Settings → Backup to see the export flow (no network involved).

Contact: milovane7777@gmail.com
```

---

## 10. 제출

1. 버전 페이지 맨 위 **「심사를 위해 제출」**
2. 수출 규정 질문이 뜨면 → **암호화를 사용하지 않음 / 아니요**
3. 광고 식별자(IDFA) 질문이 뜨면 → **아니요** (광고 SDK가 없습니다)
4. 「자동으로 릴리스」 vs 「수동으로 릴리스」 → **수동으로 릴리스** 권장
   (승인 후 담당자가 직접 공개 시점을 정할 수 있습니다)

제출하면 상태가 **「심사 대기 중」**으로 바뀝니다. 보통 **24~48시간** 안에 결과가 나옵니다.

---

## 11. 문제 해결

| 증상 | 원인과 조치 |
|---|---|
| Transporter: "Invalid Signature" | IPA를 다시 받으십시오. 압축을 풀었다가 다시 묶으면 서명이 깨집니다 |
| Transporter: "No suitable application records" | §1의 앱 레코드를 아직 안 만들었거나 번들 ID가 다릅니다 |
| 빌드가 TestFlight에 안 보임 | 30분까지 걸립니다. 그 뒤에도 없으면 Apple이 보낸 거부 메일을 확인하십시오 |
| "Missing Compliance" 배너 | 빌드 옆 **관리** → 암호화 **사용 안 함** 선택 |
| 스크린샷 "크기가 맞지 않음" | 다른 폴더의 파일을 올렸습니다. §6의 표에서 폴더와 칸을 다시 맞추십시오 |
| 처방침 URL이 안 열린다고 반려 | GitHub Pages 장애입니다. 담당자에게 알려 주십시오 |
| 「기본 언어를 잘못 골랐다」 | **되돌릴 수 없습니다.** 앱 레코드를 지우고 §1부터 다시 해야 합니다 |

### 심사에서 물어볼 가능성이 있는 것

**"손님의 알레르기 정보를 저장하는데 의료 앱 아닌가?"**
→ 아닙니다. 미용사가 직접 적는 업무 메모이며, 진단·처방·의학적 조언을 제공하지 않습니다.
연령 등급의 「의료/치료 정보」를 **아니요**로 둔 이유가 이것입니다.

**"데이터를 수집하지 않는다는 게 사실인가?"**
→ 사실입니다. §9 메모에 적은 내용을 그대로 안내하시면 됩니다.

---

## 12. 제출 후 남은 일 (담당자 몫 아님)

- 승인되면 App Store Connect에서 **「이 버전 릴리스」** 클릭
- Android(Google Play) 등록은 **별도 작업**입니다. 이 문서는 iOS 전용입니다
