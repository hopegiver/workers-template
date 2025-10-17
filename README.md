# Cloudflare Workers Template

회사 표준 Cloudflare Workers 템플릿입니다.

> **⚠️ 중요: AI 개발자는 개발 시작 전 반드시 [CONTRIBUTING.md](CONTRIBUTING.md)를 읽어주세요.**
> 모든 코드는 이 가이드의 규칙을 따라야 합니다.

## 기술 스택

- **Hono** - Web Framework
- **JWT** - 인증
- **Cloudflare Workers** - Runtime

## 시작하기

### 1. 프로젝트 생성

```bash
# 새 프로젝트 폴더로 클론
git clone https://github.com/hopegiver/workers-template.git my-project
cd my-project

# 의존성 설치
npm install
```

### 2. 개발 가이드 읽기 (필수)

**개발 시작 전 반드시 [CONTRIBUTING.md](CONTRIBUTING.md)를 읽어주세요.**

이 문서에는 다음 내용이 포함되어 있습니다:
- ✅ 코딩 컨벤션 (파일명, 클래스명 규칙)
- ✅ 아키텍처 패턴 (서비스 레이어, 라우트 패턴)
- ✅ Cloudflare 바인딩 사용법 (D1, KV, R2)
- ✅ AI 개발 가이드 (7가지 핵심 규칙)

**AI 개발 시**: 새로운 코드를 작성하기 전 CONTRIBUTING.md의 규칙을 먼저 참조하여 일관성을 유지하세요.

## 빠른 시작

### 1. 개발 서버 실행

```bash
npm run dev
```

- API: http://localhost:8787
- Swagger 문서: http://localhost:8787/docs

### 2. 배포

```bash
# JWT_SECRET 설정 (최초 1회)
wrangler secret put JWT_SECRET --env production

# 배포
wrangler deploy --env production
```

## 주요 엔드포인트

### 공개
- `GET /health` - 헬스체크
- `GET /docs` - API 문서
- `POST /auth/login` - 로그인

### 인증 필요 (JWT)
- `GET /` - 루트
- `GET /users` - 사용자 목록
- `GET /users/profile` - 프로필

## 로그인 (테스트용)

```bash
curl -X POST http://localhost:8787/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "admin123"}'
```

**테스트 계정**:
- Username: `admin` / Password: `admin123`
- Username: `user` / Password: `user123`


## 프로젝트 구조

```
src/
├── routes/       # API 라우트
├── services/     # 비즈니스 로직 (클래스)
├── utils/        # 유틸리티 함수
├── middleware/   # 미들웨어
└── index.js      # 엔트리 포인트
```

## 환경 변수

### 로컬 개발 (`.dev.vars`)
```
JWT_SECRET=your-secret-key
```

### Production (Wrangler Secrets)
```bash
wrangler secret put JWT_SECRET --env production
```

## 라이센스

ISC
