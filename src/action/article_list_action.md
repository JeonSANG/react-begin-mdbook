# 記事一覧

## 📌 개요

전체 기사 목록을 페이징 처리와 함께 보여줍니다.
`기사 상세 화면`으로 이동하거나, `新規投稿` 버튼을 통해 새 게시글 작성이 가능합니다.
Redux를 통해 페이징 상태를 관리하며, `PageScreen` 컴포넌트를 통해 페이지 네비게이션을 제공합니다.


## 🧩 컴포넌트 정보

| 항목              | 내용                                        |
|-------------------|---------------------------------------------|
| **컴포넌트명**     | ArticleList                               |
| **파일 경로**      | src/components/ArticleList.jsx                 |


## 🔄 state와 상수

| 변수명                | 설명                                  |
|------------------------|-----------------------------------------|
| articleInfoList      | 기사 일람 정보보을 저장하는 상태               |
| nowPage              | 현재 페이지 번호 상태 (`useState`)      |
| getPaging            | Redux에서 가져온 페이징 정보 (`paging`)           |
| displayRecordMaxCount| 한 페이지에 표시할 최대 기사 수 (`5`)   |
| displayMaxPageCount  | 페이징 바에 표시할 최대 페이지 수 (`5`) |


## 📚 페이지 네비게이션 함수
`PageScreen` 컴포넌트에서 페이지네이션 버튼을 클릭 시 `redux`의 `paging` 상태를 직접 디스패치하고 <br>
`ArticleList` 컴포넌트에서 `useEffect()`으로 `currentPage` 상태를 감시하고 있기 때문에 <br>
하기의 함수들은 `ArticleList` 컴포넌트에서 삭제해도 좋을 것 같습니다.

### 🔹 `prevPage()`
현재 페이지가 1이 아닌 경우 실행, 이전 페이지 번호를 표시함.

```js
const prevPage = () => {
    if (getPaging.currentPage > 1) {
        fetchData(Math.max(getPaging.currentPage - displayMaxPageCount, 1));
    }
};
```


### 🔹 `nextPage()` - 미구현
현재 페이지가 마지막 페이지가 아닐 때만 동작, 다음 페이지 번호를 표시함.

```js
// 현재
const nextPage = () => {

};

// ↓ 구현안

const nextPage = () => {
  if (getPaging.currentPage !== getPaging.totalPage) {
    fetchData(getPaging.currentPage + 1);
  }
};

```

### 🔹 `lastPage()`
현재 페이지가 마지막 페이지가 아닐 때만 동작, 마지막 페이지 번호를 표시함.

```js
const lastPage = () => {
    if (getPaging.currentPage !== getPaging.totalPage) {
        fetchData(getPaging.totalPage);
    }
};
```

### 🔹 `firstPage()`
현재 페이지가 첫 페이지가 아닐 때만 동작, 1 페이지를 표시함.

```js
const firstPage = () => {
    if (getPaging.currentPage !== 1) {
        fetchData(1);
    }
};

```

### 🔹 `changeNowPage()`
숫자 페이지 버튼을 눌렀을 때 호출됨, 현재 페이지 숫자를 누르면 처리 스킵

```js
const changeNowPage = (page) => {
    if (page !== getPaging.currentPage) {
        fetchData(page);
    }
};
```

## 🖥️ 화면 전이 함수

### 🔹 `moveMenu()`
情報一覧メニュー 화면으로 이동

```js
const moveMenu = () => {
  navigate('/menu');
};
```

### 🔹 `moveCreate()`
記事投稿 화면으로 이동

```js
const moveCreate = () => {
  navigate('/articleRegist', { state: { nowPage } });
};
```

### 🔹 `moveDetail()`
記事詳細 화면으로 이동

```js
const moveDetail = (articleId) => {
  navigate('/ArticleDetail', { state: { articleId, nowPage } });
};
```

### 🔹 `logOut()`
로그인 화면으로 이동

```js
const logOut = () => {
  navigate('/');
};
```

## 📘 기사 일람 정보 취득

### 🔹 `fetchData()`

### ① 서버에 파라미터 페이지(pageNo)의 일람 정보를 요청

📄 [記事情報一覧API 설계서](../api/article_list_api.md)

```js
const response = await axios.get('/api/article_servlet/articleList', {
    params: {
        currentPageNum: pageNo,
        maxRecordCount: displayRecordMaxCount,
        maxPageCount: displayMaxPageCount,
    }
});
```

### ② redux에서 관리하는 페이지네이션 state를 레스폰스 값으로 갱신

```js
const dispatch = useDispatch();
const data = response.data;

dispatch(setPaging({
    currentPage: data.currentPage,
    startPage: data.startPage,
    endPage: data.endPage,
    totalPage: data.totalPage,
    totalCount: data.totalCount,
    displayMaxPage: displayMaxPageCount,
}));
```


### ③ state를 레스폰스 값으로 기사 일람, 현재 페이지 state 갱신
```js
const [articleInfoList, setArticleInfoList] = useState([]);
const [nowPage, setNowPage] = useState(1);

setArticleInfoList(data.infoList);
setNowPage(data.currentPage);
```