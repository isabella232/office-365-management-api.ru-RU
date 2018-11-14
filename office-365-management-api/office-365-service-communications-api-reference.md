---
ms.TocTitle: Office 365 Service Communications API reference (preview)
title: Справочник по API сообщений о службах Office 365 (предварительная версия)
description: 'Этот API используется для доступа к следующим данным: список служб, текущее состояние, изменения состояния, сообщения.'
ms.ContentId: d0b9341a-b205-5442-1c20-8fb56407351d
ms.topic: reference (API)
ms.date: 09/05/2018
ms.openlocfilehash: cde34da7377c5d4820d6ca62dd3affe806eda229
ms.sourcegitcommit: 525c0d0e78cc44ea8cb6a4bdce1858cb4ef91d57
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2018
ms.locfileid: "25834921"
---
# <a name="office-365-service-communications-api-reference-preview"></a>Справочник по API сообщений о службах Office 365 (предварительная версия)

> [!NOTE] 
> В этой документации рассмотрены функции, доступные в предварительной версии.

С помощью API сообщений о службах Office 365 версии 2 можно получать доступ к следующим данным:

- **Получение служб.** Получение списка подписанных служб.
    
- **Получение текущего состояния.** Обновляемое в реальном времени представление текущих инцидентов и событий обслуживания.
    
- **Получение сведений об изменении состояния.** Представление журнала работоспособности служб, включающего инциденты и события обслуживания.
    
- **Получение сообщений.** Поиск сообщений об инцидентах и плановом обслуживании, а также данных Центра сообщений.
    
В настоящее время API сообщений о службах Office 365 содержит данные о следующих службах: Dynamics CRM, Dynamics Marketing, Exchange Online, Exchange Online Protection, служба идентификации, служба управления мобильными устройствами, Центр администратора партнера Office 365, OneDrive для бизнеса, Parature, OneDrive для бизнеса, Power BI для Office 365, служба управления правами, SharePoint Online, служба администратора SHD, Skype для бизнеса, Social Engagement и Yammer корпоративный.

## <a name="the-fundamentals"></a>Основные сведения

URL-адрес API включает идентификатор клиента, ограничивающий область действия операций одним клиентом:

```http
https://manage.office.com/api/v1.0/{tenant_identifier}/ServiceComms/{operation}
```

**API сообщений о службах Office 365** — это служба REST, позволяющая разрабатывать решения на любом языке и в любой среде внешнего размещения, поддерживающей сертификаты HTTPS и X.509. Этот API использует службу **Microsoft Azure Active Directory** и протокол **OAuth2** для проверки подлинности и авторизации. Чтобы получить доступ к API из приложения, необходимо сначала зарегистрировать его в Azure AD и задать подходящую область разрешений. Благодаря этому приложение сможет запрашивать маркеры доступа OAuth2, необходимые для вызова API. Дополнительные сведения о регистрации и настройке приложения в Azure AD см. в статье [Начало работы с API управления Office 365](get-started-with-office-365-management-apis.md).

Для всех запросов к API необходим заголовок Authorization HTTP с действительным маркером доступа JWT OAuth2, полученным из Azure AD и содержащим утверждение **ServiceHealth.Read**. А идентификатор клиента должен быть таким же, как в корневом URL-адресе.

```json
Authorization: Bearer {OAuth2 token}
```

**Заголовки запросов**

Ниже показаны поддерживаемые заголовки запросов для всех операций API сообщений о службах Office 365.

|Заголовок|Описание|
|:-----|:-----|
|**Accept (необязательный)**|Ниже показаны допустимые представления отклика.<br/>**application/json;odata.metadata=full**<br/>**application/json;odata.metadata=minimal**<br/>**application/json;odata.metadata=none** [используется по умолчанию, если заголовок не указан]|
|**Authorization (обязательный)**|Маркер авторизации (токен носителя JWT Azure AD) для запроса.|


<br/>

**Заголовки откликов**

Ниже показаны заголовки откликов, возвращаемые для всех операций API сообщений о службах Office 365.

|Заголовок|Описание|
|:-----|:-----|
|**Content-Length**|Длина основного текста отклика.|
|**Content-Type**|Представление отклика:<br/>**application/json**<br/>**application/json;odata.metadata=full**<br/>**application/json;odata.metadata=minimal**<br/>**application/json;odata.metadata=none**<br/>**odata.streaming=true**|
|**Cache-Control**|Используется для указания директив, которым должны подчиняться все механизмы кэширования в цепочке запросов и откликов.|
|**Pragma**|Поведение для конкретных реализаций.|
|**Expires**|Указывает, когда клиент должен сделать ресурс устаревшим.|
|**X-Activity-Id**|Созданный сервером идентификатор действия.|
|**OData-Version**|Поддерживаемая версия OData (4.0).|
|**Date**|Дата отправки отклика с сервера (в формате UTC).|
|**X-Time-Taken**|Время, затраченное на создание отклика (мс).|
|**X-Instance-Name**|Идентификатор экземпляра Azure, используемого для создания отклика (в целях отладки).|
|**Server**|Сервер, используемый для создания отклика (в целях отладки).|
|**X-ASPNET-Version**|Версия ASP.Net, используемая на сервере, который создал отклик (в целях отладки).|
|**X-Powered-By**|Технологии, используемые на сервере, который создал отклик (в целях отладки).|

<br/>

Ниже представлены операции API сообщений о службах Office 365.


## <a name="get-services"></a>Получение служб

Возвращает список подписанных служб.

||Служба|Описание|
|:-----|:-----|:-----|
|**Путь**| `/Services`||
|**Параметр запроса**|$select|Выбор подмножества свойств.|
|**Отклик**|Список объектов Service|Объект Service содержит свойства Id (String), DisplayName (String) и FeatureNames (список String).|

#### <a name="sample-request"></a>Пример запроса

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Services 
Authorization: Bearer {AAD_Bearer_JWT_Token}

```

#### <a name="sample-response"></a>Пример отклика

```json
{
    "value": [
        {
            "Id": "Exchange",
            "DisplayName": "Exchange Online",
            "FeatureNames": [
                "Sign-in",
                "E-Mail and calendar access",
                "E-Mail timely delivery",
                "Management and Provisioning",
                "Voice mail"
            ]
        },
        {
            "Id": "Lync",
            "DisplayName": "Lync Online",
            "FeatureNames": [
                "Audio and Video",
                "Federation",
                "Management and Provisioning",
                "Sign-In",
                "All Features",
                "Dial-In Conferencing",
                "Online Meetings",
                "Instant Messaging",
                "Presence",
                "Mobility"
            ]
        }
    ]
}

```


## <a name="get-current-status"></a>Получение текущего состояния

Возвращает текущее состояние службы.

||Служба|Описание|
|:-----|:-----|:-----|
|**Путь**| `/CurrentStatus`||
|**Фильтр**|Workload|Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).|
|**Параметр запроса**|$select|Выбор подмножества свойств.|
|**Отклик**|Список объектов WorkloadStatus.|Объект WorkloadStatus содержит свойства Id (String), Workload (String), StatusTime (DateTimeOffset), WorkloadDisplayName (String), Status (String), IncidentIds (список String) и FeatureGroupStatusCollection (список объектов FeatureStatus).<br/><br/>Объект FeatureStatus содержит свойства Feature (String), FeatureGroupDisplayName (String) и FeatureStatus (String).|

#### <a name="sample-request"></a>Пример запроса

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/CurrentStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a>Пример отклика

```json
{
    "value": [
        {
            "Id": "Exchange",
            "Workload": "Exchange",
            "StatusDate": "2015-04-11T00:00:00Z",
            "WorkloadDisplayName": "Exchange Online",
            "Status": "ServiceOperational",
            "IncidentIds": [],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "Signin",
                    "FeatureGroupDisplayName": "Sign-in",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Access",
                    "FeatureGroupDisplayName": "E-Mail and calendar access",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Delivery",
                    "FeatureGroupDisplayName": "E-Mail timely delivery",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Provisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "UnifiedMessaging",
                    "FeatureGroupDisplayName": "Voice mail",
                    "FeatureStatus": "ServiceOperational"
                }
            ]
        },
        {
            "Id": "Lync",
            "Workload": "Lync",
            "StatusDate": "2015-04-11T00:00:00Z",
            "WorkloadDisplayName": "Lync Online",
            "Status": "ServiceOperational",
            "IncidentIds": [],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "AudioVideo",
                    "FeatureGroupDisplayName": "Audio and Video",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Federation",
                    "FeatureGroupDisplayName": "Federation",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "ManagementandProvisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Sign-In",
                    "FeatureGroupDisplayName": "Sign-In",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "All",
                    "FeatureGroupDisplayName": "All Features",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "DialInConferencing",
                    "FeatureGroupDisplayName": "Dial-In Conferencing",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "OnlineMeetings",
                    "FeatureGroupDisplayName": "Online Meetings",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "InstantMessaging",
                    "FeatureGroupDisplayName": "Instant Messaging",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Presence",
                    "FeatureGroupDisplayName": "Presence",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Mobility",
                    "FeatureGroupDisplayName": "Mobility",
                    "FeatureStatus": "ServiceOperational"
                }
            ]
        }
    ]
}

```


## <a name="get-historical-status"></a>Получение сведений об изменении состояния

Возвращает сведения об изменении состояния службы по дням за определенный диапазон времени.

||Служба|Описание|
|:-----|:-----|:-----|
|**Путь**| `/HistoricalStatus`||
|**Фильтры**|Workload|Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).|
||StatusTime|Фильтрация по дням после StatusTime (DateTimeOffset, значение по умолчанию: 7 дней для ge CurrentTime).|
|**Параметр запроса**|$select|Выбор подмножества свойств.|
|**Отклик**|Список объектов WorkloadStatus.|Объект WorkloadStatus содержит свойства Id (String), Workload (String), StatusTime (DateTimeOffset), WorkloadDisplayName (String), Status (String), IncidentIds (список String) и FeatureGroupStatusCollection (список объектов FeatureStatus).<br/><br/>Объект FeatureStatus содержит свойства Feature (String), FeatureGroupDisplayName (String) и FeatureStatus (String).|

#### <a name="sample-request"></a>Пример запроса

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/HistoricalStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a>Пример отклика

```json
{
    "value": [
        {
            "Id": "Exchange",
            "Workload": "Exchange",
            "StatusDate": "2015-04-11T00:00:00Z",
            "WorkloadDisplayName": "Exchange Online",
            "Status": "ServiceOperational",
            "IncidentIds": [],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "Signin",
                    "FeatureGroupDisplayName": "Sign-in",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Access",
                    "FeatureGroupDisplayName": "E-Mail and calendar access",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Delivery",
                    "FeatureGroupDisplayName": "E-Mail timely delivery",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Provisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "UnifiedMessaging",
                    "FeatureGroupDisplayName": "Voice mail",
                    "FeatureStatus": "ServiceOperational"
                }
            ]
        },
        {
            "Id": "Exchange",
            "Workload": "Exchange",
            "StatusDate": "2015-04-10T00:00:00Z",
            "WorkloadDisplayName": "Exchange Online",
            "Status": "InformationAvailable",
            "IncidentIds": [
                "EX20870"
            ],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "Signin",
                    "FeatureGroupDisplayName": "Sign-in",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Access",
                    "FeatureGroupDisplayName": "E-Mail and calendar access",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Delivery",
                    "FeatureGroupDisplayName": "E-Mail timely delivery",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Provisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "UnifiedMessaging",
                    "FeatureGroupDisplayName": "Voice mail",
                    "FeatureStatus": "InformationAvailable"
                }
            ]
        }
    ]
}


```


## <a name="get-messages"></a>Получение сообщений

Возвращает сообщения о службе за определенный диапазон времени. Используйте фильтр по типу, чтобы просмотреть сообщения об инцидентах обслуживания, плановом обслуживании или из Центра сообщений.

||Служба|Описание|
|:-----|:-----|:-----|
|**Путь**| `/Messages`||
|**Фильтры**|Workload|Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).|
||StartTime|Фильтрация по времени начала (DateTimeOffset, значение по умолчанию: 7 дней для ge CurrentTime).|
||EndTime|Фильтрация по времени окончания (DateTimeOffset, значение по умолчанию: le CurrentTime).|
||MessageType|Фильтрация по MessageType (String, значение по умолчанию: all).|
||ID|Фильтрация по идентификатору (String, значение по умолчанию: all).|
|**Параметр запроса**|$select|Выбор подмножества свойств.|
||$top|Выбор максимального количества результатов (используемое по умолчанию и максимальное значение: $top=100).|
||$skip|Пропуск определенного количества результатов (значение по умолчанию: $skip=0).|
|**Отклик**|Список объектов Message.|Объект Message содержит свойства Id (String), StartTime (DateTimeOffset), EndTime (DateTimeOffset), Status (String), Messages (список объектов MessagHistory), LastUpdatedTime (DateTimeOffset), Workload (String), WorkloadDisplayName (String), Feature (String), FeatureDisplayName (String), MessageType (Enum, значение по умолчанию: all).<br/><br/>Объект MessageHistory содержит свойства PublishedTime (DateTimeOffset), MessageText (String).|

#### <a name="sample-request"></a>Пример запроса

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Messages
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a>Пример отклика

```json
{
 {
    "value": [
        {
            "Id": "EX20119",
            "Name": "EX20119",
            "Title": null,
            "StartTime": "2015-04-01T22:25:00Z",
            "EndTime": "2015-04-07T21:48:00Z",
            "Status": "Service restored",
            "Messages": [
                {
                    "PublishedTime": "2015-04-01T22:34:28.76Z",
                    "MessageText": "Current Status: Engineers are investigating an issue in which some customers may be experiencing problems accessing or using Exchange Online services or features. This event is actively being investigated. More information will be provided shortly."
                },
                {
                    "PublishedTime": "2015-04-03T18:45:32.56Z",
                    "MessageText": "Current Status: Engineers are implementing a fix within the affected infrastructure to remediate Exchange Online archive access issues. \n\nUser Experience: Affected users are unable to access online archives when using Outlook Web App (OWA). As a workaround, users may be able to access online archives via the Outlook client.\n\nCustomer Impact: Customer impact appears to be limited at this time. This issue only affects hybrid customers.\n\nPreliminary Root Cause: As part of our ongoing work, an updated certificate was deployed to the infrastructure; however, a caching issue has caused the infrastructure to use an expired certificate which is causing archive access issues.  \n\nNext Update by: Monday, April 6, 2015, at 9:00 PM UTC\n"
                },
                {
                    "PublishedTime": "2015-04-06T21:17:34.007Z",
                    "MessageText": "Current Status: Deployment of the fix is almost complete. Engineers are monitoring service health to ensure the issue has been remediated. \n\nUser Experience: Affected users are unable to access online archives when using Outlook Web App (OWA). As a workaround, users may be able to access online archives via the Outlook client. \n\nCustomer Impact: Customer impact appears to be limited at this time. This issue only affects hybrid customers.\n\nPreliminary Root Cause: As part of our ongoing work, an updated certificate was deployed to the infrastructure; however, a caching issue has caused the infrastructure to use an expired certificate which is causing archive access issues. \n\nNext Update by: Tuesday, April 7, 2015, at 10:00 PM UTC "
                },
                {
                    "PublishedTime": "2015-04-08T21:54:49.06Z",
                    "MessageText": "Final Status: Engineers have implemented a fix which remediated end-user impact. \r\n\r\nUser Experience: Affected users were unable to access online archives when using Outlook Web App (OWA).\r\n\r\nCustomer Impact: Customer impact appears to have been limited. This issue only affected hybrid customers.\r\n\r\nIncident Start Time: Monday, March 30, 2015, at 9:28 AM UTC\r\n\r\nIncident End Time: Tuesday, April 7, 2015, at 8:00 PM UTC\r\n\r\nPreliminary Root Cause: As part of our ongoing work, an updated certificate was deployed to the infrastructure; however, a caching issue has caused the infrastructure to use an expired certificate which is causing archive access issues.  \r\n\r\nNext Steps: The following is a list of known action item(s) associated with this incident. As part of the Office 365 problem management process, additional engineering actions may be identified to improve the overall service.\r\n- Action: Review the monitoring infrastructure for improvements as this event was reported by customers before an alert prompted a high priority investigation. \r\n\r\nA post-incident report will be available on the Service Health Dashboard within five business days."
                }
            ],
            "LastUpdatedTime": "2015-04-08T21:54:49.55Z",
            "Workload": "Exchange Online",
            "WorkloadDisplayName": "Exchange",
            "Feature": "Access",
            "FeatureDisplayName": "E-Mail and calendar access"
        },
        {
            "Id": "EX20789",
            "Name": "EX20789",
            "Title": null,
            "StartTime": "2015-04-06T20:00:00Z",
            "EndTime": "2015-04-07T23:00:00Z",
            "Status": "Service restored",
            "Messages": [
                {
                    "PublishedTime": "2015-04-07T23:26:44.643Z",
                    "MessageText": "Final Status: Engineers have validated that the deployed fix has resolved the issue and that service is restored.\r\n\r\nUser Experience: Affected users were unable to send or receive email while using Exchange Web Services (EWS) on their mobile devices.\r\n\r\nCustomer Impact: Customer impact appeared to be limited during this event. This issue was only affecting customers that use third-party Mobile Device Management software from Good Technology. As a workaround to provide immediate relief from impact, engineers implemented a configuration change for customers who reported this issue to Microsoft Support.\r\n\r\nIncident Start Time: Wednesday, April 1, 2015, at 2:00 PM UTC\r\n\r\nIncident End Time: Tuesday, April 7, 2015, at 10:00 PM UTC\r\n\r\nPreliminary Root Cause: As part of our ongoing efforts to improve service resiliency, an update was deployed to the infrastructure that facilitates connections from multiple Exchange Online protocols to mailbox databases. The update, however, contained a code issue that caused connectivity issues in some scenarios. \r\n\r\nNext Steps: The following is a list of known action item(s) associated with this incident. As part of the Office 365 problem management process, additional engineering actions may be identified to improve the overall service.\r\n- Action: Review the infrastructure update process to prevent reoccurrences of this scenario.\r\n\r\nPlease consider this service notification the final update on the event."
               }
            ],
            "LastUpdatedTime": "2015-04-07T23:26:45.08Z",
            "Workload": "Exchange Online",
            "WorkloadDisplayName": "Exchange",
            "Feature": "Access",
            "FeatureDisplayName": "E-Mail and calendar access"
        }
    ]
}

```


## <a name="errors"></a>Ошибки

Когда служба обнаруживает ошибку, она возвращает отправителю вызова соответствующий код отклика, используя стандартный синтаксис кодов ошибок HTTP. Согласно [спецификации OData версии 4](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html) дополнительные сведения включены в текст запроса, вернувшего код ошибки, в виде одного объекта JSON. Ниже представлен пример полного текста ошибки JSON.


```json

{ 
    "error":{ 
        "code":"AF5000.  An internal server error occurred.",
        "message": "Retry the request." 
    } 
}

```
