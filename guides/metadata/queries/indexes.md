---
related_endpoints:
  - post_metadata_queries_execute_read
category_id: metadata
subcategory_id: metadata/5-queries
is_index: false
id: metadata/queries/indexes
rank: 6
type: guide
total_steps: 7
sibling_id: metadata/queries
parent_id: metadata/queries
next_page_id: metadata/queries/comparison
previous_page_id: metadata/queries
source_url: >-
  https://github.com/box/developer.box.com/blob/main/content/guides/metadata/5-queries/6-indexes.md
fullyTranslated: true
---
# インデックス

規模を考慮したことにより、メタデータテンプレートが10,000を超えるファイルまたはフォルダに適用されている場合、メタデータクエリによって`HTTP 403`エラーが返される可能性があります。検索インデックスを作成すると、特定の検索クエリでこのエラーを解決することができます。

<Message notice>

Boxは、将来この制限を廃止するのではなく、引き上げる予定です。

</Message>

## インデックスのリクエスト

<Message info>

現時点では、検索インデックスを作成するには、[Boxメタデータクエリチーム](mailto:metadata-query-feedback@box.com)にお問い合わせいただく必要があります。

</Message>

To create an index, we will need to be informed of the intended query to be run, including the exact values for the `from​`, `​query​`, and `​order_by​` parameters of the request.

An index will then be created and you will be provided with the the name of this index. If you prefer to specify a name for the index please provide that name upon requesting the index.

Indexes are automatically applied during the metadata querying process when more than 10,000 files or folders are being searched. No further action beyond creating the index is needed to have the index applied.

<Message warning>

`LIKE`、`ILIKE`、`NOT LIKE`、および`NOT ILIKE`演算子は、インデックスのクエリでは使用できません。

</Message>

### インデックスリクエストの例

以下は、インデックスのリクエストの例です。`​from`、`query`および`order_by​`パラメータに関するすべての情報を含める必要があります。

<!-- markdownlint-disable line-length -->

|            |                                                                            |
| ---------- | -------------------------------------------------------------------------- |
| クエリの説明     | 特定のアカウント番号に関連付けられ、ステータスが保留中になっている、「顧客による送信」というタイプのファイルを返します。応答は送信日で並べられます。 |
| `from`     | `enterprise_123456.customerInfo`                                           |
| `query`    | `accountNumber = :argAccountNum AND status = :argStatus`                   |
| `order_by` | `[{ "field_key": "submissionDate","direction": "desc" }]`                  |

<!-- markdownlint-enable line-length -->

[support]: https://community.box.com/t5/custom/page/page-id/BoxSearchLithiumTKB
