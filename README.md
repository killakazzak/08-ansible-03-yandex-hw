## Описание

Данный Ansible playbook предназначен для установки и настройки Clickhouse и LightHouse на удалённых серверах. Он выполняет следующие основные задачи:

1. Устанавливает Clickhouse, загружая необходимые RPM-пакеты и создавая базу данных.
2. Устанавливает и настраивает LightHouse, включая установку Nginx и конфигурацию веб-сервера для обслуживания статических файлов LightHouse.

## Параметры

Playbook использует следующие переменные:

- `clickhouse_version`: Версия Clickhouse, которую необходимо установить. Должна быть указана в формате, например, `22.3.3.3`.
- `clickhouse_packages`: Список пакетов Clickhouse, которые необходимо загрузить. Например:
  ```yaml
  clickhouse_packages:
    - clickhouse-client
    - clickhouse-server
  ```


## Использование

Для запуска playbook используйте следующую команду:

```bash
ansible-playbook -i prod.yml site.yml --extra-vars "clickhouse_version=22.3.3.3 clickhouse_packages=['clickhouse-client', 'clickhouse-server']" --tags "clickhouse"
```


## Примечания

- Убедитесь, что у вас есть доступ к удалённым серверам и необходимые права для установки пакетов и изменения конфигураций.
- Перед запуском playbook рекомендуется проверить и настроить файлы шаблонов, такие как `nginx-lighthouse.conf.j2`, чтобы они соответствовали вашим требованиям.

