# MVP仕様（RECORE OSS Clone）

## 1. ドメインモデル

### Item（商品）
- `id` (UUID)
- `sku` (string)
- `jan` (string, optional)
- `name` (string)
- `condition` (enum: `new`, `used-a`, `used-b`, `junk`)
- `purchase_price` (number)
- `sale_price` (number)
- `status` (enum: `draft`, `in_stock`, `sold`, `returned`, `archived`)

### InventoryMovement（在庫移動）
- `id` (UUID)
- `item_id` (UUID)
- `from_location` (string)
- `to_location` (string)
- `moved_at` (datetime)
- `moved_by` (string)

### Purchase（仕入）
- `id` (UUID)
- `supplier_name` (string)
- `purchased_at` (datetime)
- `lines` (array)

### Sale（販売）
- `id` (UUID)
- `customer_id` (UUID, optional)
- `sold_at` (datetime)
- `total_amount` (number)
- `lines` (array)

## 2. API一覧（最小）

- `POST /items` 商品作成
- `GET /items/{id}` 商品取得
- `GET /items` 商品検索
- `POST /movements` 在庫移動
- `POST /purchases` 仕入登録
- `POST /sales` 販売登録
- `GET /health` ヘルスチェック

## 3. 非機能要件（初期）

- API応答: p95 < 300ms（ローカル単体）
- タイムゾーン: UTC保存 + 表示側変換
- 監査ログ: 重要更新イベントをJSONで記録
- 可観測性: `request_id` をすべてのレスポンスに付与

## 4. 将来拡張

- 店舗横断在庫引当
- 外部ECモール連携
- 帳票（買取明細・納品書・請求書）
- RBAC / ABAC
