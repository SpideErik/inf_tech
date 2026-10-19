# Лекционные материалы

В этой папке собраны конспекты тем дисциплины: что разбирали на лекции,
какие термины ввели, что делали на занятии и что после занятия появилось
в сквозном проекте. Под каждой темой есть ссылки на презентацию, страницу
материалов и документацию сервисов.

Файлы, которые раздавались на занятиях (стенды, код, CSV, шаблоны отчётов),
лежат отдельно, в папке [`materials`](../materials/README.md), по одной
папке на тему.

## Темы

| Тема | Конспект | Файлы занятия | Задание в репозитории |
|---|---|---|---|
| 1 · Вводное занятие | [tema-01](tema-01-vvodnaya.md) | [materials/tema-01](../materials/tema-01-vvodnaya/) | — |
| 2 · Цифровая воронка | [tema-02](tema-02-cifrovaya-voronka.md) | [materials/tema-02](../materials/tema-02-cifrovaya-voronka/) | [`lesson_01`](../lesson_01/README.md), часть 1 [`lesson_02`](../lesson_02/README.md) |
| 3 · UTM-метки | [tema-03](tema-03-utm-metki.md) | [materials/tema-03](../materials/tema-03-utm-metki/) | метки проверяются в [`lesson_03`](../lesson_03/README.md) |
| 4 · Google Analytics 4 | [tema-04](tema-04-google-analytics-4.md) | [materials/tema-04](../materials/tema-04-google-analytics-4/) | часть 2 [`lesson_02`](../lesson_02/README.md) |
| 5 · Свой сайт, Vercel и Google Tag | [tema-05](tema-05-vercel-google-tag.md) | [materials/tema-05](../materials/tema-05-vercel-google-tag/) | [`lesson_03`](../lesson_03/README.md) |
| 6 · События и параметры GA4 | [tema-06](tema-06-ga4-events.md) | [materials/tema-06](../materials/tema-06-ga4-events/) | [`lesson_04`](../lesson_04/README.md) |
| 7 · Контролируемая таблица заявок | [tema-07](tema-07-google-sheets-leads.md) | [materials/tema-07](../materials/tema-07-google-sheets-leads/) | [`lesson_05`](../lesson_05/README.md) |
| 8 · Google Таблицы: подготовка данных | [tema-08](tema-08-google-sheets-cleaning.md) | [materials/tema-08](../materials/tema-08-google-sheets-cleaning/) | [`lesson_06`](../lesson_06/README.md) |
| 9 · Instagram → ManyChat → заявка | [tema-09](tema-09-instagram-manychat.md) | [materials/tema-09](../materials/tema-09-instagram-manychat/) | [`lesson_07`](../lesson_07/README.md) |
| 10 · GA4: отчёты и исследования | [tema-10](tema-10-ga4-explorations.md) | [materials/tema-10](../materials/tema-10-ga4-explorations/) | задание выдаётся отдельно |
| 10.2 · DataLens: GA4 и заявки | [tema-10-2](tema-10-2-datalens.md) | [materials/tema-10-2](../materials/tema-10-2-datalens/) | задание выдаётся отдельно |
| 11 · HubSpot CRM | [tema-11](tema-11-hubspot-crm.md) | [materials/tema-11](../materials/tema-11-hubspot-crm/) | задание выдаётся отдельно |

Все презентации открываются со страницы дисциплины:
https://algorthimization-course-vvodnoe.vercel.app/op03-informacionnye-tehnologii/index.html

## Сквозной проект: что собрано по темам

За курс собирается одна система «Цифровая воронка и автоматизация заявок».
Каждая тема добавляет к ней один участок. Ниже перечислено, что после
каждой темы есть у вас в проекте.

```text
ссылка с UTM ─▶ сайт на Vercel ─▶ Google Tag ─▶ GA4: события, отчёты, исследования
                     │
                     └─▶ форма ─▶ Apps Script ─▶ Google Таблица leads ─▶ leads_clean
                                                         │
Instagram ─▶ ManyChat ─▶ guide.html ─────────────────────┤
                                                         ├─▶ DataLens: общий дашборд
                                                         └─▶ HubSpot CRM: Contact и Deal
```

| После темы | Что есть в проекте |
|---|---|
| 2 | карта воронки из семи станций, журнал событий из панели Network, список точек разрыва |
| 3 | справочник UTM-меток и набор размеченных ссылок |
| 4 | свой аккаунт GA4, ресурс, веб-поток и Measurement ID `G-…` |
| 5 | своя копия шаблона `ga4-analytics-lab` на GitHub, сайт на Vercel, Google Tag на всех страницах, `page_view` в Realtime |
| 6 | события `generate_lead` и `cta_click`, четыре метрики из `js/metrics.js`, разрез `button_name`, ключевое действие |
| 7 | таблица `GA4 Analytics Lab — Leads`, приёмник Apps Script, форма сайта пишет заявки вместе с UTM |
| 8 | таблица `leads_cleaning`: листы `source`, `leads_clean`, `check` и очищенный CSV |
| 9 | страница `guide.html`, автоматизация ManyChat на комментарий «ГАЙД», заявка из Instagram в таблице |
| 10 | заполненный шаблон анализа: Reports, Free form, сегменты, Funnel и Path по своему ресурсу |
| 10.2 | дашборд DataLens из трёх вкладок: трафик GA4, заявки из таблицы, сводная таблица по source и campaign |
| 11 | HubSpot: Pipeline из пяти стадий, шесть свойств сделки, импорт заявок из CSV, Notes и Tasks |
