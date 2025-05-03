# 記事情報一覧

- **URL**: `/api/article_servlet/articleList`
- **Method**: `GET`
- **Request Parameter**:

| 필드명          | 타입   | 데이터사이즈  |  설명       |
|:---------------|:-------|:-----------|:------------|
| currentPageNum | Number | -          | 현재 페이지   |
| maxRecordCount | Number | -          | 최대 표시건 수 |
| maxPageCount   | Number | -          | 최대 페이지 수 |

### ✅ 성공 응답 필드

| 필드명    | 타입   | 설명           |
|:----------|:-------|:-------------|
| articleId | Number | 기사 고유 ID |
| title     | String | 기사 제목    |
| createdAt | String | 작성일시     |

### ❌ 오류 코드

| 코드  | 에러 메세지 |
|:-----|:-----------|
| -    | -          |