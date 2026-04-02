#Mentorship
```mermaid
erDiagram
USER {
  int user_id PK
}

COURSE {
  int course_id PK
}

MENTOR_ASSIGNMENT {
  int mentor_id PK,FK
  int learner_id PK,FK
  int course_id PK,FK
}

MENTOR_EVALUATION {
  int evaluation_id PK
  int mentor_id FK
  int learner_id FK
  decimal score
  string comments
}

USER ||--o{ MENTOR_ASSIGNMENT : mentor
USER ||--o{ MENTOR_ASSIGNMENT : learner
COURSE ||--o{ MENTOR_ASSIGNMENT : context
USER ||--o{ MENTOR_EVALUATION : mentor
USER ||--o{ MENTOR_EVALUATION : learner

