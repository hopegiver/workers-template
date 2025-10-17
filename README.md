# Cloudflare Workers Template

회사 표준 Cloudflare Workers 템플릿입니다.

## 기술 스택

- **Hono** - Web Framework
- **JWT** - 인증
- **Cloudflare Workers** - Runtime

## 빠른 시작

### 1. 설치

```bash
npm install
```

### 2. 개발 서버 실행

```bash
npm run dev
```

- API: http://localhost:8787
- Swagger 문서: http://localhost:8787/docs

### 3. 배포

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

## 개발 가이드

상세한 개발 가이드는 [CONTRIBUTING.md](CONTRIBUTING.md)를 참고하세요.

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
