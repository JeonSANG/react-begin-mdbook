# ページネーション

## 📌 개요

페이지 번호 UI를 보여주고, 페이지 이동을 트리거하는 역할을 합니다.


## 🧩 컴포넌트 정보

| 항목              | 내용                                        |
|-------------------|---------------------------------------------|
| **컴포넌트명**     | PageScreen                               |
| **파일 경로**      | src/components/PageScreen.js                 |


## 📚 페이지 번호 생성 함수

### 🔹 `setPages()`
`redux`의 페이징 상태에서 `startPage`와 `endPage`를 이용하여 페이지 번호 생성

```js
const setPages = React.useMemo(() => {
  let pages = [];
  let startPage = getPaging.startPage;
  let endPage = getPaging.endPage;

  if (endPage === 0) {
    pages = [1];
  } else {
    for (let num = startPage; num <= endPage; num++) {
      pages.push(num);
    }
  }
  return pages;
}, [getPaging.startPage, getPaging.endPage]);
```

## 📚 페이지 네비게이션 함수
`redux` 페이징 상태의 `currentPage`를 갱신함함

### 🔹 `prevPage()`
```js
const prevPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: getPaging.currentPage - 1 });
};
```

### 🔹 `nextPage()`
```js
const nextPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: getPaging.endPage + 1 });
};
```

### 🔹 `lastPage()`
```js
const lastPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: getPaging.totalPage });
};
```

### 🔹 `firstPage()`
```js
const firstPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: 1 });
};
```

### 🔹 `changeNowPage()`
```js
const changeNowPage = (page) => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: page });
};
```

