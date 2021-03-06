# Поиск и удаление JndiLookup класса из уязвимых библиотек Log4j

## Общее описание

Роль создает отчет о наличии уязвимых версий на хосте с указанием полного пути до библиотеки и ее версии, и отправкой по почте.

!!! help "Справка"
    По умолчанию создается только отчет, удаление класса не производится.

!!! info "Для информации"
    Перед удалением класса, сценарий сохраняет копию файла по тому же пути и стем же именем как у оригинального файла с добавлением суффикса `.orig`.

!!! attention "Внимание"
    Удаление класса необходимо проводить с осторожностью. Не рекомендуется применять данный метод по умолчанию.

## Параметры

| Название переменной | Тип переменной | Значения по умолчанию | Описание                                                    |
| :------------------ | :------------: | :-------------------: | :---------------------------------------------------------- |
| log4j_fix           |    boolean     |         undef         | Удаляет класс из уязвимых библиотек.                        |
| mail_host           |     string     |         undef         | Адрес почтового сервера через который идет отправка письма. |
| mail_from           |     string     |         undef         | Почтовый адрес отправителя.                                 |
| mail_rcpt_to        |     string     |         undef         | Почтовый адрес получателя.                                  |

!!! help "Справка"
    В RHSatellite/Katello переменные `mail_host`, `mail_from` добавленны как глобальные. При запуске роли с RHSatellite/Katello их не надо прописывать.

!!! fail "Особое внимание"
    Не рекомендуется использовать автоматическое удаление класса.

## Теги

Не используются.

## Примеры

!!! example "inventory/hosts"
    ``` ini
    [example-servers]
    <host_name> ansible_ssh_host=<host_ip> ansible_ssh_user=<user_name_for_connect>

    [example-servers:vars]
    ansible_connection=ssh
    mail_host='10.10.1.1'
    mail_rcpt_to='admin@exampe.com'
    #log4j_fix=true
    ```
