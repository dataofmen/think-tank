이 폴더는 Telegram Bot이 전처리한 입력을 Claude Code로 전달하기 위한 임시 저장소입니다.

## 파일 형식

- `pending-YYYYMMDD-HHMMSS.json`: Bot이 생성한 intake 요청
- 처리 완료 후 `.processed/`로 이동됩니다.

## 예시

```json
{
  "timestamp": "2026-03-26T14:30:00",
  "user_id": 123456789,
  "username": "myusername",
  "type": "article_url",
  "content": {
    "title": "기사 제목",
    "content": "본문 내용...",
    "images": ["https://example.com/image1.jpg"],
    "url": "https://example.com/article"
  }
}
```

## 처리 방법

Cursor에서 이 폴더를 모니터링하고, 새 파일이 생기면:
1. 파일 읽기
2. `/intake` 스킬 자동 실행
3. 4단계 검증
4. 저장
5. 파일을 `.processed/`로 이동
