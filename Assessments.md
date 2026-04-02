#Assessments

```mermaid
erDiagram
USER {
  int user_id PK
}

COURSE {
  int course_id PK
}

ASSESSMENT {
  int assessment_id PK
  int course_id FK
  string type
  int pass_mark
  int max_attempts
}

QUESTION {
  int question_id PK
  int assessment_id FK
  string text
  string type
}

ATTEMPT {
  int attempt_id PK
  int assessment_id FK
  int user_id FK
  decimal score
  string status
  datetime attempt_date
}

COURSE ||--o{ ASSESSMENT : has
ASSESSMENT ||--o{ QUESTION : contains
ASSESSMENT ||--o{ ATTEMPT : records
USER ||--o{ ATTEMPT : makes
