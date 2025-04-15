# 記事詳細

- **URL**: `/api/article_servlet/detail/${articleId}`
- **Method**: `GET`
- **Request Parameter**:

| 필드명     | 타입    | 데이터사이즈  |  설명         |
|:----------|:-------|:------------|:--------------|
| articleId | Number | 10          | 조회할 기사 ID |

### ✅ 성공 응답 필드

| 필드명    | 타입   | 설명         |
|:----------|:-------|:-------------|
| articleId | Number | 기사 고유 ID |
| title     | String | 기사 제목    |
| content   | String | 기사 내용    |
| userId    | String | 작성자 ID    |
| createdAt | String | 작성일시    |


### ❌ 오류 코드

| 코드  | 에러 메세지                             |
|:-----|:--------------------------------------|
| 400  | 記事詳細情報を取得時に問題が発生しました。|
| 500  | サーバー（DB）側でエラーが発生しました。  |