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
## SPAの特徴

#### 従来のWebアプリケーションのフロー

1. ユーザーがUI上でアクションを起こす
2. サーバーへ送信
3. サーバーが受け取り遷移先のHTMLを送信
4. サーバーからHTMLを受け取り画面遷移

---
<!-- class: default -->

# SPAの特徴

#### SPAのフロー

1. ユーザーがUI上でアクションを起こす
2. アクションに必要なデータのみをサーバーから要求
3. 返却値(JSON形式)をもとに処理
4. 差分があった一部を更新

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
- コンポーネントベース
- どこでも使える

---
<!-- class: lead -->
<!-- header: Redux -->
# Redux

---
<!-- class: default -->
## Reduxとは

- Reactが扱うUIの状態を管理するフレームワーク
- Reducer + Flux = Redux
- Reduce → 整理して変換する

---
<!-- class: default -->
## Reduxの要素

- ActionCreator
- Action
- Store
- State
- Reducer

---
<!-- class: default -->

## Reduxの要素

- ActionCreator
- Action

```js
  {
    type: ADD_TODO,
    text: 'Add New ToDo'
  }
```

---
<!-- class: default -->
## Reduxの要素

- Store
  - アプリケーションの状態(State)を保持する場所
  - アプリケーション内で１つ存在する。

---
<!-- class: default -->
## Reduxの要素

- State
- Reducer

---
<!-- class: default -->
## Reduxのデータフロー

1. ユーザーがUI(View)から入力を行いActionを作成
    - ActionCreator
    - Action
2. ActionをStoreへdispatch(発信)する
    - Store
3. dispatchされたActionとStateをReducerへ渡す
    - State
    - Reducer
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
