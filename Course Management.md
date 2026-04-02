#Course Management

```mermaid
erDiagram
COURSE {
  int course_id PK
  string title
  string description
  string type
  boolean is_mandatory
  int expiry_months
  int created_by FK
}

COURSE_VERSION {
  int version_id PK
  int course_id FK
  string version_number
  string status
}

MODULE {
  int module_id PK
  int version_id FK
  string title
  int order_index
  boolean is_required
}

CONTENT {
  int content_id PK
  int module_id FK
  string type
  string url
}

PREREQUISITE {
  int course_id PK,FK
  int prerequisite_course_id PK,FK
}

LAB_SESSION {
  int session_id PK
  int course_id FK
  int facilitator_id FK
  datetime date_time
  string location
  int capacity
}

ASSESSMENT {
  int assessment_id PK
  int course_id FK
  string type
  int pass_mark
  int max_attempts
}

COURSE ||--o{ COURSE_VERSION : has
COURSE_VERSION ||--o{ MODULE : contains
MODULE ||--o{ CONTENT : includes
COURSE ||--o{ LAB_SESSION : schedules
COURSE ||--o{ ASSESSMENT : has
COURSE }o--o{ PREREQUISITE : has
