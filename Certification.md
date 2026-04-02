#Certification

```mermaid
erDiagram
USER {
  int user_id PK
}

COURSE {
  int course_id PK
}

CERTIFICATE {
  int certificate_id PK
  int user_id FK
  int course_id FK
  datetime issue_date
  datetime expiry_date
  string verification_code
  string file_url
}

EXTERNAL_CERTIFICATION {
  int ext_cert_id PK
  int user_id FK
  string provider
  string status
  datetime expiry_date
}

USER ||--o{ CERTIFICATE : earns
COURSE ||--o{ CERTIFICATE : issues

USER ||--o{ EXTERNAL_CERTIFICATION : has