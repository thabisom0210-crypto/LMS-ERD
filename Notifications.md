#Notifications

```mermaid
erDiagram
USER {
  int user_id PK
}

ENROLMENT {
  int enrolment_id PK
}

NOTIFICATION {
  int notification_id PK
  int user_id FK
  string type
  string message
  string status
  datetime sent_at
}

REMINDER {
  int reminder_id PK
  int user_id FK
  int enrolment_id FK
  string type
  datetime schedule_date
}

USER ||--o{ NOTIFICATION : receives
USER ||--o{ REMINDER : receives
ENROLMENT ||--o{ REMINDER : about
