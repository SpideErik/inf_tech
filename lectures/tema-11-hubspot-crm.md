# Тема 11 · HubSpot CRM: от заявки к процессу

**Презентация:** https://algorthimization-course-vvodnoe.vercel.app/op03-informacionnye-tehnologii/lessons/11-hubspot-crm/index.html

**Материалы:** https://algorthimization-course-vvodnoe.vercel.app/op03-informacionnye-tehnologii/lessons/11-hubspot-crm/materials.html

**Файлы занятия:** [materials/tema-11-hubspot-crm](../materials/tema-11-hubspot-crm/) —
CSV для импорта, контрольный CSV, карта свойств, подготовка в Google Таблицах,
отчёт сверки.

## Содержание лекции

### Зачем CRM

Таблица заявок хранит факт обращения. Работа с клиентом — звонки, заметки,
задачи, смена этапов — ведётся в **CRM** (Customer Relationship Management).
В CRM у каждого человека одна карточка, а у каждого обращения — своя сделка.

### Модель данных HubSpot

| Понятие | Значение |
|---|---|
| Object | тип записей: Contacts, Companies, Deals, Tickets |
| Record | одна запись: конкретный контакт или сделка; у каждой есть Record ID |
| Property | поле записи: Email, Deal stage, Request ID |
| Association | связь между записями: контакт ↔ сделка |
| Pipeline | последовательность этапов работы со сделками |
| Stage | этап воронки со своей вероятностью закрытия |

Заявка становится парой **Contact + Deal**. Один человек — один Contact
(ищется по Email). Каждое обращение — новый Deal, связанный с этим Contact.

### Pipeline Applications

| Stage | Вероятность |
|---|---|
| New application | 10 % |
| In progress | 30 % |
| Contacted | 60 % |
| Done | Won, 100 % |
| Rejected | Lost, 0 % |

### Свойства сделки

Шесть своих Deal Properties: Request ID и UTM Source / Medium / Campaign
(однострочный текст), Direction (выпадающий список backend, frontend,
data), Application Created At (дата и время). На тарифе Free своих свойств
не больше 10 в сумме. Request ID — обычное текстовое поле, HubSpot
не проверяет по нему дубли.

### Импорт из CSV

CSV готовится в Google Таблицах из `leads_clean`: 12 столбцов, включая
Pipeline и Deal stage. Импорт — **Advanced import → Contacts + Deals →
Single file**:

- Contacts: создать или обновить по Email;
- Deals: только создать;
- все 12 колонок сопоставлены свойствам (mapping);
- формат даты YMD, часовой пояс Europe/Moscow.

Application Created At — время заявки на сайте; Create date — время
создания записи в CRM. Если в строке ошибка отдельного свойства, сделка
могла создаться; перед повторным импортом её находят и обновляют
по Record ID.

### Работа со сделкой

Карточки сделок на доске (Board) перетаскиваются между стадиями. К сделке
добавляют владельца, **Note** (заметку) и **Task** (задачу со сроком
и исполнителем). **Saved View** сохраняет фильтр, например все сделки
из Instagram. Смена стадии в CRM не меняет статус в таблице и дашборде:
синхронизации пока нет, её настраивают в разделе автоматизации n8n.

## Что делали на занятии

1. Вручную создали тестовый Contact «Иван Тестов» и записали его Record ID.
2. Настроили Pipeline Applications с пятью стадиями.
3. Создали шесть свойств сделки и записали внутренние имена
   в `property-map.csv`.
4. Подготовили CSV в Google Таблицах по `sheets-preparation.md`.
5. Импортировали три заявки: получили три Contacts и три Deals, Иван
   остался прежним Contact.
6. Провели REQ-001 через стадии с Note и Task до Done, REQ-002 перевели
   в Rejected с причиной в Note.
7. Сохранили View `UTM Source = instagram`, `UTM Campaign = backend_guide`.
8. Импортировали `repeat_contact.csv` с повторным обращением: у Ивана стало
   две сделки, всего четыре Deals.
9. Заполнили `reconciliation.md`.

## Что вошло в проект

- CRM HubSpot с процессом обработки заявок и импортированными сделками.
- CRM — станция 8 маршрута; в разделе 3 курса записи в неё будут создаваться
  автоматически через n8n.

## Документация

- [HubSpot: подготовка файла импорта](https://knowledge.hubspot.com/import-and-export/set-up-your-import-file)
- [Импорт нескольких объектов](https://knowledge.hubspot.com/import-and-export/import-objects)
- [Как работает инструмент импорта](https://knowledge.hubspot.com/import-and-export/understand-the-import-tool)
- [Properties](https://knowledge.hubspot.com/properties/create-and-edit-properties)
- [Pipeline и стадии](https://knowledge.hubspot.com/object-settings/set-up-and-customize-pipelines)
- [Лимиты тарифов](https://legal.hubspot.com/hubspot-product-and-services-catalog)
- [Задачи и представления](https://knowledge.hubspot.com/tasks/filter-tasks-and-manage-task-views)
