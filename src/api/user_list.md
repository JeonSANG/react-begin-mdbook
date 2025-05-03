# 会員一覧

- **URL**: `/api/profile_servlet/usersList`
- **Method**: `GET`
- **Request Parameter**:

| 필드명          | 타입   | 데이터사이즈  |  설명       |
|:---------------|:-------|:-----------|:------------|
| currentPageNum | Number | -          | 현재 페이지   |
| maxRecordCount | Number | -          | 최대 표시건 수 |
| maxPageCount   | Number | -          | 최대 페이지 수 |


### ✅ 성공 응답 필드

| 필드명     | 타입    | 설명         |
|:----------|:-------|:------------|
| userId    | String | ユーザーID   |
| name      | String | 氏名         |
| email     | String | メールアドレス |
| authority | String | 権限          |

### ❌ 오류 코드

| 코드  | 에러 메세지 |
|:-----|:-----------|
| -    | -          |