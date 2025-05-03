# 記事削除

- **URL**: `/api/article_servlet/delete`
- **Method**: `DELETE`
- **Request Parameter**:

| 필드명      | 타입        | 데이터사이즈 | 설명         |
|:----------|:------------|:-----------|:-------------|
| articleId | Number      |10          | 기사 고유 ID |
| userId    | String      |-           | 작성자 ID    |
| authority | String      |-          |유저 권한 (admin/user) |

### ✅ 성공 응답 필드

| 필드명 | 타입 | 설명 |
|:------|:----|:----|
| -     | -   | -   |

### ❌ 오류 코드

| 코드 | 에러 메세지 |
|:----|:-----------|
| -   | -          |
