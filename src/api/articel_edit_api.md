# 記事編集

- **URL**: `/api/article_servlet/edit`
- **Method**: `PUT`
- **Request Parameter**:

| 필드명      | 타입        | 데이터사이즈 | 설명         |
|:----------|:------------|:-----------|:-------------|
| articleId | Number      |10          | 기사 고유 ID |
| title     | String      |100         | 기사 제목    |
| content   | String      |1000        | 기사 내용    |
| userId    | String      |-           | 작성자 ID    |


### ✅ 성공 응답 필드

| 필드명 | 타입 | 설명 |
|:------|:----|:----|
| -     | -   | -   |

### ❌ 오류 코드

| 코드 | 에러 메세지 |
|:----|:-----------|
| -   | -          |

