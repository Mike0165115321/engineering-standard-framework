# FUNCTION-SERVICE

> มาตรฐาน service layer — business logic + orchestration

## Service Rules

1. **Service ไม่รู้จัก HTTP** — ไม่ import request/response, ไม่ใช้ status code
2. **Service เรียก repository ผ่าน DI** — ไม่ instantiate repository เอง
3. **1 service = 1 entity / 1 use case** — ไม่รวมทุกอย่างไว้ใน service เดียว
4. **Service จัดการ transaction** — เปิด/ปิด/rollback ที่ service layer
5. **Service คืน StandardResponse** — ไม่ raise HTTP exception

## Service Function Pattern

```python
def function_name(self, request: RequestDTO) -> StandardResponse:
    # 1. validate (ถ้าต้องการ business validation ที่เกินจาก controller)
    # 2. authorize (check permission)
    # 3. execute (call repository / external service)
    # 4. return StandardResponse
```

## Standard Response Format

```python
@dataclass
class StandardResponse:
    success: bool
    data: Any = None
    error: ErrorDetail = None

@dataclass
class ErrorDetail:
    code: str        # เช่น "NOT_FOUND", "VALIDATION_ERROR"
    message: str     # human-readable
    details: dict = None  # optional field-level errors
```
