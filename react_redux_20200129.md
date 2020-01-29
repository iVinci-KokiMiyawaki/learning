---
marp: true
theme: gaia
paginate: true
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
---
<!-- class: lead -->
![bg 50%](https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg)

![bg 30%](https://raw.githubusercontent.com/reduxjs/redux/master/logo/logo.png)

# **React/Reduxに触れるための一歩**

株式会社 i-Vinci - 宮脇 光輝

---
<!-- class: default -->
<!-- header: Agenda -->
## Agenda

1. 今回の目標
2. SPA
3. React
4. Redux

---
<!-- class: default -->
<!-- header: SPA -->
## 今回の目標

- SPA(React)の特徴を認識する
- Reduxのデータフローを理解する

---
<!-- class: lead -->
<!-- header: SPA -->
# SPA

---
<!-- class: default -->
## SPAとは

#### SPAとは、「Single Page Application」の略

#### 単一のページで構成されるWebアプリケーション

---
<!-- class: default -->
<!-- _footer: 引用元:[https://miyach.in/programming/spa-basis/] -->
#### 従来のWebアプリケーションのフロー

![bg 100%](https://miyach.in/wp-content/uploads/2019/02/612f43071a2a0f44423b8bcb86c93e1a-1024x455.png)

---
<!-- class: default -->
<!-- _footer: 引用元:[https://miyach.in/programming/spa-basis/] -->
#### SPAのフロー

![bg 100%](https://miyach.in/wp-content/uploads/2019/02/7fb8f1c748d490339c64aa37f2515920-1024x455.png)

---
<!-- class: lead -->
<!-- header: React -->
# React

---
<!-- class: default -->
## Reactとは

- JavaScriptでUIを構築するためのフロントエンドフレームワーク

---
<!-- class: default -->
## Reactの特徴

- 宣言的なView
  - データによって構造が崩れにくい
  - 仮想DOMを用いての差分を再描画
  - JSX記法が使える
- コンポーネントベース
  - HTML, CSS, JavaScriptをコンポーネントとして管理
  - 構造がわかりやすい

---
<!-- class: lead -->
<!-- header: Redux -->
# Redux

---
<!-- class: default -->
## Reduxとは

- Reactが扱うUIの状態を管理するフレームワーク
- Redux → Reducer + Flux
- Reduce → **整理して変換する**

---
<!-- class: default -->
## Reduxの要素

- ActionCreator
- Action
- Reducer
- Store
- State

---
<!-- class: default -->
### ActionCreator
  - Actionを作成する関数
```js
  import { createAction } from 'redux-actions';
  export const setUserName = createAction(SET_USER_DATA);
```

### Action
  - 処理を行うための情報を持ったオブジェクト
```js
  {
    type: 'SET_USER_DATA',
    name: 'Tanaka Taro'
  }
```

---
<!-- class: default -->
### Reducer
  - ActionとStateから新しくStateを作成し返す関数
  - 元のStateは更新しない
  - Stateの更新内容は必ず
```js
import { handleActions } from 'redux-actions';
export default handleActions({
  [TYPE.SET_USER_DATA]: (state, action) => ({
    ...state,
    name: action.payload.name,
  }),
});
```

---
<!-- class: default -->
### Store
  - アプリケーションの状態(State)を保持する場所
    - ※読み取り専用
  - Stateにアクセス、更新を行うための関数も持っている。

### State
  - アプリケーションでの状態を表す
  - 

---
<!-- class: default -->
## Reduxのデータフロー

1. ユーザーがUI(View)から入力を行いActionを作成
2. ActionをStoreへdispatch(発信)する
3. dispatchされたActionとStateをReducerへ渡す
4. Reducerが作成した新しいStateを保存

---
<!-- class: default -->
<!-- _footer: 引用元:[https://staltz.com/unidirectional-user-interface-architectures.html] -->
## Reduxのデータフロー

![bg 50%](https://s3.amazonaws.com/media-p.slid.es/uploads/364812/images/2484790/ARCH-Redux2-extended-real-declerative.gif)

---
<!-- class: default -->
## Reduxの三原則

- Single source of truth (信頼できる唯一の情報源)
  - アプリケーションの全てのstateを単一のStoreで保持する。
- State in read-only(Stateは読み取り専用にする)
  - Stateの変更は必ずActionを経由して行う。
- Changes are made with pure functions(変更はすべて純粋関数)
  - StateがどのActionによってどのように変更されるかは、Reducerで定義する。
  - Reducerは純粋関数で定義する。
