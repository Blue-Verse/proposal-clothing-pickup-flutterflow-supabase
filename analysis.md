# 의류 수거 서비스 앱/웹 개발 (Flutterflow + Supabase) — 제안 분석 로그

> 생성일: 2026-05-07
> 공고 URL: https://www.wishket.com/project/155122/
> 지원 마감: 2026-05-15
> 예상 시작: 2026-05-18

## 1. 공고 파싱 결과

```yaml
job:
  title: "의류 수거 서비스 앱/웹 개발(Flutterflow/Supabase)"
  category: "개발 / 웹·Android·iOS / IT 서비스 구축"
  budget_range: "10,000,000원"
  duration: "50일"
  applicants: 14
  deadline: "2026-05-15"
  start_date: "2026-05-18"
  classification: "운영 중인 서비스의 리뉴얼 또는 유지보수"
  planning_state: "필요한 내용을 간단히 정리한 상태"
  client_experience: "IT 프로젝트 관리 경험 없음"
  collaboration: "현재 어드민 구축 및 유지보수 개발자 1명 (적극 협조 어려움)"
  priorities:
    - 1순위: 산출물 완성도
    - 2순위: 금액
    - 3순위: 일정 준수
  current_service: "pickot.kr (아임웹 호스팅)"
  migration_target: "아임웹 → Flutterflow + Supabase"
  tech_stack:
    - Flutterflow (iOS/Android/Web 동시)
    - Supabase (DB + 인증)
    - 토스페이먼츠 (결제)
    - 카카오 알림톡 (블룸 AI 채널)
    - Strapi (현재 어드민 — 유지)
  required_features:
    - 회원가입/로그인 (이메일 + 카카오 소셜)
    - 수거 신청 폼 (날짜·시간·주소·품목·메모)
    - 수거 신청 내역 조회 + 상태 추적 (접수→수거중→완료 등)
    - 마이페이지 (내 신청 히스토리)
    - 관리자 페이지 (현재 strapi 사용 중)
    - 카카오 알림톡 (상태 변경 시 자동 발송)
    - 기존 회원 데이터 이전
    - 쇼핑몰 기능
  references:
    - 리클 (recl.co.kr)
    - 뉴오프 (new-off.com)
  deliverables:
    - 소스 코드 원본
  client_questions: []
  job_post_url: "https://www.wishket.com/project/155122/"
```

## 2. URL/이미지 분석

### pickot.kr (현재 운영 사이트)
- **서비스**: 비대면 의류 수거 + 의류 업사이클링 플랫폼
- **수거 시스템**: 서울은 비대면 방문 수거, 서울 외는 수거 키트 신청 후 회수
- **포인트(픽포인트)**: 의류 수거 → 픽포인트 적립 → 픽옷스토어 구매 차감
- **픽옷스토어 카테고리**: 식품 / 생활용품 / 패션의류 / ECO / R'era MADE(업사이클) / 뷰티
- **UI/UX 패턴**: 상단 네비 + 좌측 네비, 로그인/비로그인 분기, 타임세일·품절 배지
- **고객지원**: 카카오톡 채널 실시간 응대
- **공지/이벤트**: 진행 중 이벤트 + 공지사항 게시판

### 리클(recl.co.kr)
- 모바일 앱 기반 헌 옷 수거 서비스 + Refty(쇼핑) 통합
- 메뉴 구성: 리클 소개·액티브 리클·헌 옷 수거·Refty·고객지원·채용
- → 모바일 앱 + 쇼핑 통합 구조 표준 제시

### 뉴오프(new-off.com, 구 newoff.co.kr 리다이렉트)
- 중고 의류 마켓 + 내옷팔기(C2C 판매자 기능)
- 매일 정오 신상품 업데이트, 명품/일반 브랜드 가격대 22K~399K원
- → 중고 의류 마켓 + 사용자 판매 기능 표준 제시

### 도출된 추가 요구사항 (텍스트엔 없으나 레퍼런스 분석으로 식별)
- 픽포인트 적립/사용 이코노미(수거→적립→쇼핑 차감)
- 수거 키트 배송 플로우(서울 외 지역)
- 쇼핑몰 6종 카테고리 + 타임세일/품절 배지
- 이벤트/공지 게시판
- 카카오톡 채널 고객지원 연계

## 3. 실현 가능성 분석 (내부용 — 클라이언트 비공개)

| 항목 | 값 |
|------|-----|
| 프로젝트 유형 | 모바일 앱(Flutterflow) + 결제 + 데이터 마이그레이션 |
| Feasibility 등급 | 조건부 가능 (모바일 +20% / 결제 +15% / 마이그레이션 +5%) |
| 기본 공수 (AI 보조 없이) | 60 M/D |
| AI 절감률 적용(50%) | 30 M/D |
| 버퍼 +20% (모바일·결제·마이그레이션) | 36 M/D |
| 달력 변환 (× 7/5 주말 보정) | 50.4일 ≒ 50일 |
| 클라이언트 예상 기간 | 50일 |
| 차이 | 거의 일치 → 클라이언트 기간 그대로 사용 |
| 판정 | **수주 권장** — 산출물 완성도 우선 + 마이그레이션 검증 강조 |

### 기본 공수 산정 내역
- 기획/설계: 5 M/D
- 디자인 검토: 2 M/D (Figma 준비 완료)
- FE (Flutterflow): 27 M/D
- BE (Supabase): 21 M/D
- QA/배포: 5 M/D
- **합계: 60 M/D → AI 50% 절감 → 30 M/D → 버퍼 20% → 36 M/D**

## 4. 포트폴리오 매칭

| 순위 | 프로젝트 | 매칭 점수 | 핵심 매칭 근거 |
|------|---------|----------|---------------|
| 1 | Calendar Share | ★★★★★ | Flutter + Supabase 듀얼 백엔드 직접 구축 (가장 핵심 매치) |
| 2 | Pilates App | ★★★★☆ | iOS·Android·Web 3 플랫폼 동시 출시 + 예약·결제·CRM·자동 알림 통합 |
| 3 | DayStarter | ★★★★☆ | Flutter 풀스코프 운영 + 포인트/리워드 이코노미 트랜잭션 정합성 |
| 후보 | Harmony Link | ★★★☆☆ | Flutter 멀티플랫폼 + 다중 사용자 역할 + 알림 |
| 후보 | Fortune App | ★★★☆☆ | Flutter + Firebase + 광고 SDK + 포인트/체크인 리워드 |

**최종 선정**: Calendar Share, Pilates App, DayStarter

## 5. 최종 제안 요약

- **지원 금액**: 8,500,000원 (VAT 별도) — 클라이언트 예상 1,000만원 × 85%
- **지원 기간**: 50일 — 클라이언트 예상 그대로
- **핵심 제안 포인트**:
  1. Flutter + Supabase 듀얼 백엔드 직접 구축 경험 — Flutterflow 산출 코드 위에서 Supabase 안정 통합
  2. iOS·Android·Web 3 플랫폼 동시 출시 검증된 패턴
  3. 결제 + 예약/신청 + 자동 알림 통합 운영 경험
  4. 포인트/리워드 이코노미 트랜잭션 정합성 직접 설계 경험
  5. 산출물 완성도 우선 — 마이그레이션 검증·통합 QA·1개월 무상 하자보수·인수인계 문서 포함

## 6. 최종 산출물

### 6.1 제안서 사이트 URL
https://proposal-router.claude-ai-b27.workers.dev/proposal-clothing-pickup-flutterflow-supabase/

### 6.2 지원 금액
8,500,000원 (VAT 별도)

### 6.3 지원 기간
50일 (2026-05-18 ~ 2026-07-06)

### 6.4 클라이언트 질문 답변
해당 없음 (공고에 별도 클라이언트 질문 없음)

### 6.5 지원 내용 (전문)

안녕하세요, 의류 수거 서비스 앱/웹 개발 (Flutterflow + Supabase) 프로젝트에 지원합니다.

본 프로젝트에 대한 상세 제안서(견적서, 공수계산서, PRD, 일정, 포트폴리오)를 별도 페이지로 준비하였습니다. 아래 링크에서 확인해 주시면 감사하겠습니다.
▶ 제안서 상세 페이지: https://proposal-router.claude-ai-b27.workers.dev/proposal-clothing-pickup-flutterflow-supabase/
▶ 위시켓 포트폴리오: https://www.wishket.com/partners/p/blueverse1/

---

<프로젝트 진행 제안>

■ 프로젝트 분석
- 운영 중인 픽옷(pickot.kr) 서비스를 아임웹 → Flutterflow + Supabase 독립 플랫폼으로 마이그레이션하는 리뉴얼 프로젝트
- 단일 코드베이스로 iOS·Android·반응형 웹 동시 출시, 수거 신청·상태 추적·마이페이지·쇼핑몰을 통합 구축
- 카카오 알림톡(블룸 AI 채널) 자동 발송, 토스페이먼츠 결제 연동, 기존 Strapi 어드민 데이터 연계, 회원/포인트 데이터 마이그레이션 포함
- 1순위 산출물 완성도 우선에 맞춰 마이그레이션 검증·통합 QA·인수인계 문서까지 포함하여 안정적인 컷오버 보장

■ 작업 일정 (총 50일, 4단계)

[Phase 1] Day 1–10
- 킥오프, Figma·기능 명세 리뷰
- ERD·RLS 정책·API 명세 설계
- 아임웹 → Supabase 마이그레이션 매핑 작성

[Phase 2] Day 11–25
- 이메일 + 카카오 OAuth 인증 (Supabase Auth)
- 수거 신청 폼 (날짜·시간·주소·품목·메모·사진)
- 신청 내역·상태 추적 (Supabase Realtime)
- 마이페이지 + 카카오 알림톡 자동 발송 Edge Function

[Phase 3] Day 26–40
- 쇼핑몰 (카테고리·상품·장바구니·주문)
- 토스페이먼츠 결제 + 픽포인트 적립/차감
- 아임웹 → Supabase 데이터 마이그레이션 실행 + 검증
- 기존 Strapi 어드민 데이터 연동

[Phase 4] Day 41–50
- 통합 시나리오 QA + 회귀 테스트
- iOS App Store / Google Play 심사 제출
- 웹 배포 + 도메인 컷오버
- 인수인계 문서 + 운영 가이드 전달

■ 마일스톤 및 산출물
- M1 (Day 10): 설계 완료 — ERD·RLS·API 명세·마이그레이션 플랜 승인
- M2 (Day 25): 핵심 기능 데모 — 회원가입~수거 신청~상태 추적~알림톡 End-to-End
- M3 (Day 40): 쇼핑몰·결제·마이그레이션 데모 — 토스페이먼츠 결제 + 마이그레이션 검증 리포트
- M4 (Day 50): 출시 빌드 — iOS/Android 스토어 등록 + 웹 배포 + 인수인계 문서
- 최종 산출물: Flutterflow 프로젝트 원본, Supabase 스키마/RLS/Edge Functions, API 명세서·ERD·운영 가이드, 데이터 마이그레이션 검증 리포트

■ 미팅 시 협의 필요 사항
- 관리자 페이지 범위: 기존 Strapi 유지 + 데이터 연동 vs. Supabase 기반 별도 어드민 신규 구축 — 협업 개발자 분담 영역 확정 필요
- Flutterflow Pro 라이선스 보유 여부 + 코드 익스포트 권한
- 카카오 비즈니스 채널·토스페이먼츠 가맹점 등록 상태
- 데이터 마이그레이션 범위(회원·포인트는 필수, 과거 주문 이력 포함 여부)
- 컷오버 방식 (단계적 전환 vs. 일시 컷오버) + 사용자 비밀번호 재설정 정책
- 월 단위 유지보수 계약 조건

---

<유사 프로젝트 진행 경험>

▶ 소셜 캘린더 앱 (Calendar Share) (2025.01 MVP)
- 프로젝트 유형: B2C 모바일 앱 / Flutter + Supabase 듀얼 백엔드
- 핵심 기능: Flutter 17K LOC 단일 코드베이스로 iOS·Android 45+ 화면, Firebase + Supabase 듀얼 백엔드(Auth·DB·Storage·Realtime), 7종 푸시 알림
- 유사점: Flutter + Supabase 직접 구축 경험으로 Flutterflow 산출 코드 위에 Supabase Auth/RLS/Realtime/Storage 안정 통합 가능. 듀얼 백엔드 마이그레이션 패턴 직접 운영 경험 보유.
- 기술 스택: Flutter, Dart, Supabase, Firebase, FCM, Provider

▶ 필라테스 프랜차이즈 통합 관리 앱 (2019.09–2019.12, 4개월)
- 프로젝트 유형: B2B2C 앱 / 예약·결제·CRM·자동 알림 통합
- 핵심 기능: 4개월 내 iOS·Android·반응형 웹 3 플랫폼 동시 출시, 예약·결제·CRM·매출·채팅 8개 모듈, 4단계 사용자 권한 분리
- 유사점: 모바일·웹 3 플랫폼 동시 출시 패턴 그대로 적용 가능. 수거 슬롯 예약 + 토스페이먼츠 결제 + 픽포인트 차감을 단일 트랜잭션으로 설계, 상태 변경 시 카카오 알림톡 자동 발송 구조 구현 경험.
- 기술 스택: React Native, React, Node.js, REST API, FCM/APNs, WebSocket

▶ 게이미피케이션 알람 앱 (DayStarter) (2022.06~ 운영 중)
- 프로젝트 유형: B2C 앱 / Flutter + 포인트/리워드 이코노미
- 핵심 기능: Flutter + Kotlin + NestJS, 듀얼 토큰 이코노미(적립·소비·보유), 30+ API 엔드포인트, 37 데이터 모델, 48 화면, 8개+ 외부 서비스 통합
- 유사점: 픽포인트(수거 적립 → 스토어 차감) 트랜잭션 정합성·롤백 구조 그대로 적용 가능. Flutter 풀스코프 디버깅·확장·스토어 배포 직접 수행, 외부 서비스 8개+ 동시 통합 안정화 경험.
- 기술 스택: Flutter, Kotlin, NestJS, PostgreSQL, Firebase, AdMob

---

<사용 기술과 툴>

▶ 개발 기술
- 프론트엔드: Flutterflow, Flutter / Dart
- 백엔드: Supabase (Auth · DB · Storage · Realtime · Edge Functions), PostgreSQL + RLS
- 결제·인증: 토스페이먼츠 SDK, 카카오 OAuth
- 알림: 카카오 알림톡 (블룸 AI 채널)
- 외부 연동: Strapi, 카카오 주소 API

▶ 개발 도구 및 인프라
- 버전 관리: GitHub
- CI/CD: GitHub Actions / Flutterflow 빌드 파이프라인
- 클라우드: Supabase (BaaS) + Vercel/Netlify (웹)
- 모바일 배포: Apple App Store / Google Play Console
- 모니터링: Supabase Logs / Sentry (선택)

▶ 커뮤니케이션
- 일일 진행 공유: Slack 또는 카카오톡
- 주간 미팅: Zoom / Google Meet
- 문서 공유: Notion 또는 Google Docs
- 이슈 트래킹: GitHub Issues
- 디자인 리뷰: Figma 코멘트

### 6.6 관련 포트폴리오 추천
1. 소셜 캘린더 앱 (Calendar Share) — Flutter + Supabase 듀얼 백엔드 직접 구축 (가장 핵심 매치)
2. 필라테스 프랜차이즈 통합 관리 앱 — iOS·Android·웹 3 플랫폼 동시 출시 + 예약·결제·자동 알림 통합
3. 게이미피케이션 알람 앱 (DayStarter) — Flutter 풀스코프 + 포인트/리워드 이코노미 트랜잭션 정합성
