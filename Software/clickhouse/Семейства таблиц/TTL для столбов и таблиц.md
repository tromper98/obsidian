#clickhouse 

Имеется возможность задать время жизни для столбцов и таблиц.

## TTL столбца

Когда срок действия значений в столбце истек, Clickhouse автоматически заменяет его значением по умолчанию. Если срок действия всех значений столбцов куска данных истек - происходит удлаение куска данных в файловой системе.

## TTL таблицы

Для таблицы можно задать одно выражения для устаревания данных, а также несколько условий, при срабатывании которых данные будут перемещаться на другие диски или тома. Когда некоторые данные устаревают, Clickhouse удаляет все соотвествующие строки. Операции перемешения или повторного сжатия данных выполняются только когда устаревают все данные в куске.

## Удаление устаревших данных

ClickHouse удаляет данные с истекщим TTL, когда происходит мерж данных в фоновом режиме. Если выполнить запрос SELECT между слияниями, есть риск получить устаревшие данные. Чтобы недопускать этого необходимо добавить OPTIMIZE перед SELECT.
