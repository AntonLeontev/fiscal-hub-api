# Fiscal Hub Api

## Авторизация
Передавать с каждым запросом заголовок 
`Authorization: Bearer xxx`
где ххх — токен доступа
Также обязательно нужно передавать заголовок `Accept: application/json`

## Base path
Все запросы к апи отправляются на базовый путь
https://fiscal-hub.ru/api

## Получение списка чеков
GET /v1/receipts

Ответ 200 ОК
```
{
  "current_page": 1,
  "data": [
    {
      "id": "9e3189ed-b605-4cfa-a243-993b9b8847b8",
      "external_id": "2b5deb17-06b6-40dd-bcc3-b5bedad91ec0",
      "agency_id": 1,
      "user_id": 4,
      "receipt_type": "sell refund",
      "name": "Юлий",
      "surname": "Мензулин",
      "patronymic": "Федорович",
      "passport": "4532  4567334",
      "insurer_id": 1,
      "insurer_name": "СПАО \"ИНГОССТРАХ\"",
      "insurer_inn": "7705042179",
      "contract_id": 1,
      "contract_name": "ОСАГО",
      "vat": "none",
      "contract_series": "Ттт",
      "contract_number": "6543217",
      "client_email": "example@mail.ru",
      "agent_email": "example@mail.ru",
      "amount": 13000,
      "is_draft": false,
      "payment_type": "cash",
      "status": "done",
      "error_text": null,
      "fiscal_receipt_number": "2",
      "shift_number": "6",
      "receipt_datetime": "12.02.2025 13:27:28",
      "fn_number": "7380440801037213",
      "ecr_registration_number": "0008773698015331",
      "fiscal_document_number": "16",
      "fiscal_document_attribute": "3747376176",
      "ofd_receipt_url": null,
      "submited_at": "2025-02-12T10:27:26.000000Z",
      "created_at": "2025-02-12T10:27:26.000000Z",
      "updated_at": "2025-02-12T10:27:28.000000Z",
      "user": {
        "email": "example@mail.ru",
        "name": "Юлий Мензулин",
        "id": 4
      }
    }
  ],
  "first_page_url": "https://fiscal-hub.ru/api/v1/receipts?items_per_page=1&page=1",
  "last_page_url": "https://fiscal-hub.ru/api/v1/receipts?items_per_page=1&page=6",
  "next_page_url": "https://fiscal-hub.ru/api/v1/receipts?items_per_page=1&page=2",
  "prev_page_url": null,
  "from": 1,
  "to": 1,
  "total": 6,
  "items_per_page": 1
}
```
В поле data содержится коллекция объектов Receipt.
Поля объекта Receipt

|Поле|Описание|
| --- | ------- |
| id | внутренний идентификатор |
| external_id | идентификатор в Атол |
|receipt_type|enum тип чека. значения: “sell”, "sell refund"|
|name|имя покупателя|
|surname|фамилия покупателя|
|patronymic|отчество покупателя|
|passport|номер паспорта покупателя|
|insurer_name|Название страховой компании|
|insurer_inn|ИНН страховой компании|
|contract_id||
|contract_name|Название договора страхования|
|vat|НДС|
|contract_series|Серия договора|
|contract_number|Номер договора|
|client_email||
|agent_email||
|amount|Сумма договора в копейках|
|is_draft|Признак черновика чека|
|payment_type|тип оплаты. Значения ‘cash’, ‘cashless’|
|status| статус обработки чека: wait, fail, done |
|error_text|текст ошибки, если статус fail|
|fiscal_receipt_number|Номер чека|
|shift_number|Номер смены|
|receipt_datetime|Дата чека|
|fn_number|ФН|
|ecr_registration_number|Номер аппарата|
|fiscal_document_number|ФНД|
|fiscal_document_attribute|Фискальный признак документа|
|ofd_receipt_url|ссылка на чек в ОФД|
|submited_at|Время отправки в Атол|
|created_at|Время создания|
|updated_at|Время последнего обновления|
|user|объект пользователя, пробившего чек|




