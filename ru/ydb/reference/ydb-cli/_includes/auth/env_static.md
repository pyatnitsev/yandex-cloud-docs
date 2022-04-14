---
sourcePath: ru/ydb/ydb-docs-core/ru/core/reference/ydb-cli/_includes/auth/env_static.md
---
- Если задано значение переменной окружения `YDB_USER` или `YDB_PASSWORD`, то используется режим аутентификации по логину и паролю. Логин считывается из переменной `YDB_USER`; если он не задан, то выдается ошибка `User password was provided without user name`. Пароль считывается из переменной `YDB_PASSWORD`; если она не задана, то в зависимости от наличия опции командной строки `--no-password` применяется либо пустой пароль, либо пароль будет запрошен интерактивно.