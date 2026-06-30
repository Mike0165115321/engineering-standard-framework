# FUNCTION-CRUD

> มาตรฐานฟังก์ชัน CRUD ทุก service

## Universal Rules (ใช้ทุกฟังก์ชัน)

1. **1 ฟังก์ชัน = 1 หน้าที่** — Single Responsibility
2. **20-50 บรรทัด** — ถ้าเกิน → split
3. **docstring + type hints** ทุก public function
4. **structured exception** — `raise ServiceException(code="NOT_FOUND", message="...")`
5. **log entry + exit** ทุก service function
6. **return format** — ผ่าน StandardResponse เสมอ

## CRUD Patterns

### Create
```
 validate input → check duplicate → authorize → create → return
```
- ใช้ transaction
- return created object (ไม่ใช่ plain ID)

### Read / Get By ID
```
 validate id → authorize → query → found? return : raise NOT_FOUND
```

### List / Search
```
 validate pagination → filter → query → count → return paginated response
```
- pagination format: `{page, per_page, total, total_pages, items}`
- filter ผ่าน query params

### Update
```
 validate id + input → authorize → check existence → update → return updated
```
- partial update (PATCH) หรือ full update (PUT) — กำหนดให้ชัด
- optimistic locking ถ้ามี concurrence

### Delete
```
 authorize → check existence → delete / soft-delete → return success
```
- soft-delete: `deleted_at` timestamp, ห้ามลบจริง
- cascade หรือ block — กำหนดให้ชัด

## "Reason to Change" Test

ก่อนสร้างฟังก์ชัน ถาม: "ฟังก์ชันนี้เปลี่ยนเพราะอะไรได้บ้าง?"
- ถ้าเปลี่ยนเพราะหลายเหตุผล → split
- ถ้าเปลี่ยนเพราะเหตุผลเดียว → ok

## Dependency Injection Pattern

```python
# ดี — inject dependencies
class OrderService:
    def __init__(self, repo: OrderRepository, payment: PaymentGateway):
        self.repo = repo
        self.payment = payment

# ไม่ดี — import แล้วสร้างเองใน class
class OrderService:
    def __init__(self):
        self.repo = OrderRepository()  # hardcoded
```
