# 식품 관리 프로그램 (CRUD)

## Deployment
- Vercel URL: <https://2026-oss-assign-05.vercel.app/>

## Key Learning
1. **배열 + render() 구조:** 데이터를 배열(`foods`)로 관리하고, 데이터가 바뀔 때마다 `render()`로 화면을 다시 그리는 방식을 배웠다.
2. **DOM 동적 생성과 이벤트 처리:** `createElement()`, `appendChild()`로 표를 만들고 `addEventListener()`로 버튼 동작을 연결하는 방법을 익혔다.
3. **입력값 검증(validation):** 상품 이름 필수·20자 제한, 카테고리 선택 필수 등 잘못된 입력을 막는 방법을 배웠다.

## CRUD Service
**주제:** 식품 재고를 등록·조회·수정·삭제하는 관리 프로그램

**데이터 Field**

| Field | 설명 |
|---|---|
| id | 번호  |
| product | 상품 이름 (필수, 20자 이하) |
| count | 수량 |
| price | 가격 |
| day | 유통기한 |
| category | 카테고리 (과자 / 아이스크림 / 음료 / 과일, 필수 선택) |

**구현 방법**
- **Create:** 저장 버튼을 누르면 `saveProduct()`가 입력값을 읽어 `foods.push()`로 새 객체를 추가하고 `nextId`를 1 증가시킨다.
- **Read:** `render()`가 `foods` 배열을 순회하며 `<tr>`/`<td>`를 만들어 표에 출력한다.
- **Update:** 수정 버튼을 누르면 `editProduct(index)`가 해당 값을 입력창에 채우고 `editIndex`에 위치를 저장한다. 저장 시 `editIndex`가 -1이 아니면 새로 추가하지 않고 그 항목의 값을 덮어쓴다.
- **Delete:** 삭제 버튼을 누르면 `confirm()`으로 확인한 뒤 `foods.splice(index, 1)`로 항목을 제거하고 `render()`를 다시 호출한다.

## JavaScript
- `getElementById()`: 입력창과 표의 `tbody`를 가져온다.
- `createElement()` / `appendChild()`: `tr`, `td`, 수정·삭제 버튼을 동적으로 만들어 표에 붙인다.
- `addEventListener()`: 저장·수정·삭제 버튼의 클릭 이벤트를 처리한다.
- `Array` (`push`, `splice`): 데이터를 추가하고 삭제한다.
- `render()`: 배열 내용을 화면에 다시 그려 변경 사항을 반영한다.
- `validate()`: 저장 전에 이름 비어 있음, 20자 초과, 카테고리 미선택을 검사한다.

## AI / Search Usage
- **도구:** Claude
- **사용 목적:** `saveProduct()`에서 새로 추가할 때와 수정할 때를 나눠 저장하는 방법을 이해하기 위해 사용했다.
- **코드 적용:** `find()`가 조건에 맞는 첫 번째 데이터를 반환하는 방식을 확인하고 Update 기능에 적용했다. 수정 시에는 `editIndex`로 대상 항목을 구분해 값을 덮어쓰도록 구현했다.
- **새롭게 이해한 내용:** `find()`는 조건에 맞는 첫 번째 요소를 반환하고, 배열 요소(객체)의 값을 바꾸면 원본 데이터가 수정된다는 점을 이해했다.

## Problem & Solution

| 문제 | 해결 |
|---|---|
| placeholder를 넣었을 때 입력 상자가 작아 문구가 잘 보이지 않았다. | 입력창 크기를 조정해 문구가 보이도록 했다. |
| 저장 방법이 어려웠다. `saveProduct()`에서 추가와 수정을 한 버튼으로 처리해야 했다. | `editIndex` 변수를 두고 -1이면 추가(Create), 아니면 수정(Update)으로 분기했다. 저장 후에는 `editIndex`를 -1로 되돌리고 입력창을 비웠다.(ai에게 도움 받음)|

## Reflection
- 배열 하나만 바꿔도 `render()`로 화면 전체가 갱신되는 구조가 편리하다는 것을 알게 되었다.
.
- 새로고침하면 데이터가 초기화되는데, `localStorage`나 서버를 사용해 유지하는 방법이 궁금하다.


