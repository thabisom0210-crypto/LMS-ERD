#Payments & Vouchers

```mermaid
erDiagram
USER {
  int user_id PK
}

ENROLMENT {
  int enrolment_id PK
}

PAYMENT {
  int payment_id PK
  int enrolment_id FK
  int user_id FK
  decimal amount
  string payment_type
  string status
}

VOUCHER {
  int voucher_id PK
  string code
  decimal discount
  datetime expiry_date
  int usage_limit
}

ENROLMENT ||--o{ PAYMENT : generates
USER ||--o{ PAYMENT : pays
USER ||--o{ VOUCHER : uses
