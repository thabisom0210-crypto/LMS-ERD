# User & Identity 

```mermaid
erDiagram
USER {
  int user_id PK
  string first_name
  string last_name
  string email UK
  string password_hash
  date dob
  string status
  int manager_id FK
  int department_id FK
  string external_auth_id
  datetime created_at
}

DEPARTMENT {
  int department_id PK
  string name
}

ROLE {
  int role_id PK
  string name
}

PERMISSION {
  int permission_id PK
  string name
}

USER_ROLE {
  int user_id PK,FK
  int role_id PK,FK
}

ROLE_PERMISSION {
  int role_id PK,FK
  int permission_id PK,FK
}

AUTH_LOG {
  int auth_log_id PK
  int user_id FK
  string login_method
  datetime timestamp
  string status
}

DEPARTMENT ||--o{ USER : has
USER }o--o{ ROLE : assigned
ROLE }o--o{ PERMISSION : grants
ROLE ||--o{ USER_ROLE : used_by
USER ||--o{ USER_ROLE : has
ROLE ||--o{ ROLE_PERMISSION : has
PERMISSION ||--o{ ROLE_PERMISSION : in
USER ||--o{ AUTH_LOG : logs

