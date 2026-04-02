#Reporting & Dashboards

```mermaid
erDiagram
USER {
  int user_id PK
}

ROLE {
  int role_id PK
}

REPORT {
  int report_id PK
  string type
  int created_by FK
}

SCHEDULED_REPORT {
  int schedule_id PK
  int report_id FK
  string frequency
  datetime last_run
}

DASHBOARD {
  int dashboard_id PK
  int role_id FK
  string config_json
}

USER ||--o{ REPORT : creates
REPORT ||--o{ SCHEDULED_REPORT : schedules

ROLE ||--o{ DASHBOARD : configures
