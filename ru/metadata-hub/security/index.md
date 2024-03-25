---
title: "Управление доступом в {{ metadata-hub-full-name }}"
description: "Управление доступом в сервисе {{ metadata-hub-full-name }}. В разделе описано, на какие ресурсы можно назначить роль, какие роли действуют в сервисе, какие роли необходимы для того или иного действия."
---

# Управление доступом

{% include notitle [preview](../../_includes/note-preview.md) %}

В этом разделе вы узнаете:
* [На какие ресурсы можно назначить роль](#resources).
* [Какие роли действуют в сервисе](#roles-list).
* [Какие роли необходимы](#choosing-roles) для того или иного действия.

{% include [about-access-management](../../_includes/iam/about-access-management.md) %}

## На какие ресурсы можно назначить роль {#resources}

Вы можете назначить роль на [облако](../../resource-manager/concepts/resources-hierarchy.md#cloud), [каталог](../../resource-manager/concepts/resources-hierarchy.md#folder) или на отдельное [подключение](../operations/connection-access.md). Эти роли будут действовать и на вложенные ресурсы.

## Какие роли действуют в сервисе {{ connection-manager-name }}{#roles-list}

Для управления правами доступа к подключениям вы можете использовать роли сервиса {{ metadata-hub-full-name }} (_сервисные роли_) и роли {{ yandex-cloud }} (_примитивные роли_).

### Сервисные роли для управления подключениями с помощью {{ connection-manager-full-name }} {#service-roles}

{% include [connection-manager-auditor](../../_includes/iam/roles/connection-manager-auditor.md) %}

{% include [connection-manager-viewer](../../_includes/iam/roles/connection-manager-viewer.md) %}


{% include [connection-manager-editor](../../_includes/iam/roles/connection-manager-editor.md) %}

{% include [connection-manager-admin](../../_includes/iam/roles/connection-manager-admin.md) %}



### Примитивные роли {#primitive-roles}

{% include [roles-primitive](../../_includes/roles-primitive.md) %}

### Какие роли мне необходимы {#choosing-roles}

В таблице ниже перечислено, какие роли нужны для выполнения указанного действия. Вы всегда можете назначить роль, которая дает более широкие разрешения, нежели указанная. Например, назначить `editor` вместо `viewer`.

| Действие                                                      | Необходимые роли                     |
|---------------------------------------------------------------|--------------------------------------|
| Получить информацию о подключениях                            | `connection-manager.viewer`          |
| Получить список подключений                                   | `connection-manager.viewer`          | 
| Создать подключение                                           | `connection-manager.editor`          | 
| Изменить подключение                                          | `connection-manager.editor`          |
| Удалить подключение                                           | `connection-manager.editor`          |
| Установить права доступа к подключению                        | `connection-manager.admin`           |
| Изменить права доступа к подключению                          | `connection-manager.admin`           |

## Что дальше {what-is-next}

* [Подробнее об управлении доступом в {{ yandex-cloud }}](../../iam/concepts/access-control/index.md).
* [Подробнее о наследовании ролей](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance).