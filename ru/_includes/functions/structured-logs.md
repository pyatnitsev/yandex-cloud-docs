## Структурированные логи {#structured-logs}

Кроме текстовых записей, в стандартные потоки `stdout` и `stderr` можно писать структурированные логи в следующем JSON-формате:

* `message/msg` — текст записи.
* `level` — уровень логирования. Доступные уровни логирования — `TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR` и `FATAL`.

Все поля, кроме `message/msg` и `level`, автоматически записываются в `json-payload`.

Лог должен быть однострочным. Любая запись, которая содержит поле `message/msg` и длина которой не превышает 64 КБ, считается структурированным логом. Если запись длиннее, она делится на несколько записей и считается текстовой.

Отключить структурированные логи можно, указав переменную окружения `STRUCTURED_LOGGING = false`. Тогда любой лог в JSON-формате будет считаться текстовой записью.