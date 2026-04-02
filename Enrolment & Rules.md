#Enrolment & Rules

```mermaid
erDiagram
USER {
  int user_id PK
}

COURSE {
  int course_id PK
}

ENROLMENT {
  int enrolment_id PK
  int user_id FK
  int course_id FK
  string status
  datetime due_date
  datetime completion_date
  string approval_status
}

ENROLMENT_RULE {
  int rule_id PK
  int role_id FK
  int department_id FK
  string location
  string condition_json
}

APPROVAL {
  int approval_id PK
  int enrolment_id FK
  int approver_id FK
  string status
  string comments
  datetime created_at
}

DOCUMENT {
  int document_id PK
  int enrolment_id FK
  string file_url
  string status
}

ROLE {
  int role_id PK
}

DEPARTMENT {
  int department_id PK
}

USER ||--o{ ENROLMENT : enrolls
COURSE ||--o{ ENROLMENT : includes

ENROLMENT ||--o{ APPROVAL : requires
USER ||--o{ APPROVAL : approves

ENROLMENT ||--o{ DOCUMENT : has

ROLE ||--o{ ENROLMENT_RULE : targeted_by
DEPARTMENT ||--o{ ENROLMENT_RULE : scoped_by
