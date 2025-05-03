# ページネーション

## 📌 개요

페이지 번호 UI를 보여주고, 페이지 이동을 트리거하는 역할을 합니다.


## 🖥️ 화면 항목

![](../images/ページネーション.png)
[イメージを開く](../images/ページネーション.png)

| 항목명(논리)     | 항목명(물리) | 타입     | 글자 수 (상한) | 필수 항목 | 설명                           |
|------------------|--------------|----------|----------------|-----------|--------------------------------|
| 総件数           | totalCount   | label    | - | - | 일람의 총 건수, redux paging 상태에서 관리 |
| 総ページ数       | totalPage    | label   | - | - | 일람 페이지의 총 수, redux paging 상태에서 관리 |
| 現在ページ数     | currentPage  | label   | - | - | 일람에서 표시하고 있는 현재 페이지 번호, redux paging 상태에서 관리 |
| 1ページへ        | -            | button   | - | - | 클릭 시 firstPage() 호출 |
| 前のページへ     | -            | button   | - | - | 클릭 시 prevPage() 호출 |
| ページ番号       | -            | button   | - | - | 클릭 시 changeNowPage() 호출 |
| 次のページへ     | -            | button   | - | - | 클릭 시 nextPage() 호출 |
| 最後のページへ   | -            | button   | - | - | 클릭 시 lastPage() 호출 |



## 🧩 컴포넌트 정보

| 항목              | 내용                                        |
|-------------------|---------------------------------------------|
| **컴포넌트명**     | PageScreen                               |
| **파일 경로**      | src/components/PageScreen.js                 |


## 📚 페이지 번호 생성 함수

## 🔹 `setPages()`
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

---

## 📚 페이지 네비게이션 함수
`redux` 페이징 상태의 `currentPage`를 갱신함함

## 🔹 `prevPage()`
```js
const prevPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: getPaging.currentPage - 1 });
};
```

---

## 🔹 `nextPage()`
```js
const nextPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: getPaging.endPage + 1 });
};
```

---

## 🔹 `lastPage()`
```js
const lastPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: getPaging.totalPage });
};
```

---

## 🔹 `firstPage()`
```js
const firstPage = () => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: 1 });
};
```

---

## 🔹 `changeNowPage()`
```js
const changeNowPage = (page) => {
  dispatch({ type: 'SET_CURRENT_PAGE', payload: page });
};
```

