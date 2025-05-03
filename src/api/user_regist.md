# 新規ユーザー作成API

- **URL**: `/api/profile_servlet/profile_servlet/regist`
- **Method**: `POST`
- **Request Parameter**:

| 필드명     | 타입    | 데이터사이즈  |  설명            |
|:----------|:-------|:------------|:-----------------|
| userId    | String | -           | 유저 아이디 (공란) |
| email     | String | 30          | 메일 주소         |
| password  | String | 50          | 비밀번호          |
| name      | String | 50          | 유저명            |
| authority | String | -           | 유저 권한         |

### ✅ 성공 응답 필드
| 필드명 | 타입 | 설명 |
|:------|:----|:----|
| -     | -   | -   |

### ❌ 오류 코드

| 코드  | 에러 메세지                    |
|:-----|:------------------------------|
| 400  | 既に同じメールが登録されています。|

