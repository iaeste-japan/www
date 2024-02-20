# IAESTE Japan website

## 1. About

website のリポジトリは https://www.iaeste.or.jp/ のソースコードを管理します。

## 2. Release to production and staging environment

下表の左列に記載されたブランチが更新されると、各環境 website の更新が自動的におこなわれます。

`development`, `staging` のプレビュー環境は公開していません。

| Branch name   | Environment      | URL                       |
| ------------- | ---------------- | ------------------------- |
| `development` | development      | Private                   |
| `staging`     | staging          | Private                   |
| `production`  | production       | https://www.iaeste.or.jp/ |

## 3. Branch rule

`development` ブランチ以外への Pull Request は禁止です。

### 3-1. Basic branches

| Branch name   | People who can submit pull requests | Note                                                                   |
| ------------- | ----------------------------------- | ---------------------------------------------------------------------- |
| `development` | All developers                      | base branch。基本は、この `development` ブランチに Pull Request を送ってください。 |
| `staging`     | Administrators only                 | 本番前の最終確認用。管理者以外の Pull Request は禁止です。                      |
| `production`  | Administrators only                 | 管理者以外の Pull Request は禁止です。                                      |

## 4. Plan the webpage structure

```
www.iaeste.or.jp/
├── about/
├── news/
│   ├── yyyy-MM-dd/
│   └── yyyy-MM-dd/
├── students/
├── employers/
├── internships/
│   ├── how-it-works/
│   ├── information-session/
│   ├── faqs/
│   ├── required-docs/
│   └── reports/
├── org/
│   ├── public-information/
│   ├── members/
│   └── join/
├── contact/
└── en/
    ├── internship/
    │   └── required-docs/
    └── contact/
```
