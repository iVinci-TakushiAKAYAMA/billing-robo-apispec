# まるなげ与信申請解除

指定の請求先の与信を解除（停止）します。既に与信が有効な請求先に対して実行できます。

/api/v1.0/request_marunage_credit/stop

## アウトライン

- [リクエスト](#リクエスト)
- [レスポンス](#レスポンス)
- [使用例](#使用例)
  - [リクエスト例](#リクエスト例)
  - [レスポンス例](#レスポンス例)
- [エラー](#エラー)

## リクエスト

- Method URL: `https://billing-robo.jp:10443/api/v1.0/request_marunage_credit/stop`
- Preferred HTTP method: `POST`
- Accepted content types: `application/json`
- Encode: `UTF-8`

### Parameters

| 名前                    | 概要                                   | 桁数 | 種別                                  | 必須 |
| ------------------------| -------------------------------------- | ---- | ------------------------------------- | ---- |
| user_id                 | ユーザー ID（管理画面へのログイン ID）    | 100  | [メール形式](../../index.md#種別)      | 必須 |
| access_key              | アクセスキー                            | 100  | [半角英数](../../index.md#種別)        | 必須 |
| billing_code            | 請求先コード                            |  20  |  [半角英数 + 記号](../../index.md#種別) | 必須 |

## レスポンス

- Type: `application/json`
- Encode: `UTF-8`

### Fields

| 名前                     | 概要                                    | 型      |
| -------------------------| -------------------------------------- | ------- |
| user_id                  | ユーザー ID                             | string  |
| access_key               | アクセスキー                            | string  |
| error_code               | エラーコード <br> ※正常時は null        | int    |
| error_message            | エラーメッセージ <br> ※正常時は null    | string  |
| billing_code             | 請求先コード                            | string |


## 使用例

### リクエスト例

```json
{
    "user_id": "sample@robotpayment.co.jp",
    "access_key": "xxxxxxxxxxxxxxxx",
    "billing_code": "billing_code_001"
}
```

### レスポンス例

Status: 200 OK

```json
{
    "user_id": "sample@robotpayment.co.jp",
    "access_key": "xxxxxxxxxxxxxxxx",
    "error_code": null,
    "error_message": null,
    "billing_code": "billing_code_001"
}
```

## エラー

[共通エラー](../../index.md#共通エラー)

個別エラー

| エラーコード  | 内容                                               |
| ------------ | -------------------------------------------------- |
| 5501         | まるなげオプション利用不可                           |
| 5502         | 解除対象の請求先が存在しません                        |
| 5503         | 請求先コードが不正                                   |
| 5504         | 対象の請求先与信が申請中又は停止中の為解除できません    |
| 5505         | 請求先に紐づくまるなげ与信が存在しません               |

----

[TOP へ戻る](../../index.md)