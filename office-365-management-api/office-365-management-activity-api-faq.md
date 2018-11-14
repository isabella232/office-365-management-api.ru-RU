---
ms.TocTitle: Office 365 Management Activity API frequently asked questions
title: 'Вопросы и ответы: API действий управления Office 365'
description: 'Вопросы и ответы: использование API действий управления Office 365'
ms.ContentId: ''
ms.topic: reference (API)
ms.date: 09/21/2018
ms.openlocfilehash: 612aac60ab421d79a1c866a4a79157ee255d167d
ms.sourcegitcommit: 525c0d0e78cc44ea8cb6a4bdce1858cb4ef91d57
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2018
ms.locfileid: "25834920"
---
# <a name="office-365-management-activity-api-frequently-asked-questions"></a>Вопросы и ответы: API действий управления Office 365

#### <a name="what-events-are-audited-for-a-specific-office-365-service"></a>В случае каких событий проводится аудит для определенной службы Office 365?

В документации по схеме API действий управления Office 365 приведен полный список событий. Дополнительные сведения см. в статье [Схема API действий управления Office 365](office-365-management-activity-api-schema.md).

#### <a name="how-do-i-onboard-to-the-management-activity-api"></a>Как подключиться к API действий управления?

Сведения о том, как начать работу с API действий управления Office 365, см. в статье [Начало работы с API управления Office 365](get-started-with-office-365-management-apis.md).
 
#### <a name="what-is-the-throttling-limit-for-the--management-activity-api"></a>Каково ограничение на регулирование для API действий управления?

Текущее ограничение для регулирования составляет 60 000 запросов в минуту на идентификатор издателя. 

#### <a name="we-want-to-programmatically-capture-all-events-in-all-workloads-what-is-the-most-reliable-way-to-do-this"></a>Мы хотим программным способом собирать данные обо всех событиях во всех рабочих нагрузках. Как это лучше сделать?

Это можно сделать, используя API действий управления Office 365. Рекомендуем также использовать **модель извлечения**, так как с веб-перехватчиками возникают проблемы. Дополнительные сведения см. в разделе, посвященном использованию веб-перехватчиков, из статьи [Устранение неполадок, связанных с API действий управления Office 365](troubleshooting-the-office-365-management-activity-api.md#using-webhooks).

#### <a name="is-it-true-that-mailbox-auditing-in-exchange-online-can-only-be-enabled-by-using-powershell"></a>Аудит почтовых ящиков в Exchange Online действительно можно включить только с помощью PowerShell?

Да. Но мы работаем над тем, чтобы в организации Office 365 был по умолчанию включен аудит всех почтовых ящиков. Дополнительные сведения см. в разделе, посвященном включению аудита почтовых ящиков Exchange по умолчанию, в [блоге Майкрософт о соответствии требованиям, конфиденциальности и безопасности](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Exchange-Mailbox-Auditing-will-be-enabled-by-default/ba-p/215171).

#### <a name="are-there-any-differences-in-the-records-that-are-fetched-by-the-management-activity-api-versus-the-records-that-are-returned-by-using-the-audit-log-search-tool-in-the-office-365-security--compliance-center"></a>Есть ли разница между записями, которые получены API действий управления, и записями, которые возвращены средством поиска в журналах аудита, доступным в Центре безопасности и соответствия требованиям Office 365?

В обоих случаях возвращаются одни и те же данные. Фильтрация не выполняется. Единственное отличие заключается в том, что с помощью API за один подход можно получить данные за последние 7 дней. При поиске в журнале аудита в Центре безопасности и соответствия требованиям (или при использовании соответствующего командлета [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog) в Exchange Online) можно получить данные за последние 90 дней. 
 
#### <a name="arent-webhook-notifications-more-immediate-after-all-arent-they-event-driven"></a>Разве использование уведомлений веб-перехватчиков не предполагает более быстрое получение результатов? Они же создаются при появлении событий?

Нет. Уведомления веб-перехватчиков не создаются автоматически сразу после появления событий. Нужно создать большой двоичный объект контента. Такое создание можно считать триггером доставки уведомлений. В последнее время период ожидания, предшествующий получению уведомлений, в случае использования веб-перехватчиков был дольше, чем в случае отправки API запросов непосредственно с помощью операции */content*. API действий управления не стоит рассматривать как систему оповещений о событиях безопасности в режиме реального времени. Корпорация Майкрософт предлагает другие продукты для этого. В случае обеспечения безопасности уведомления о событиях, получаемые с помощью API действий управления, больше подходят для определения тенденций использования за длительные периоды.

#### <a name="when-pulling-the-data-from-the-management-activity-api-there-is-sometimes-a-delay-of-more-than-3-to-5-days-why-is-this"></a>При извлечении данных из API действий управления иногда происходит задержка, длящаяся дольше 3–5 дней. Почему это происходит?

Иногда в службе Office 365 поваляются экземпляры временных сбоев или другие проблемы. В этом случае некоторые записи аудита удаляются, и служба пытается выполнить их обратную засыпку. Хотя такое происходит только с 5–10 % записей, в некоторых ситуациях именно с этими записями может быть связана задержка. Если такая задержка длится более 5 дней, ознакомьтесь с данными на панели мониторинга работоспособности служб в Центре администрирования Office 365. При необходимости также можно отправить запрос в [службу поддержки Майкрософт](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online).

#### <a name="i-am-encountering-a-throttling-error-in-the-management-activity-api-what-should-i-do"></a>У меня возникла ошибка регулирования в API действий управления. Что делать?

Отправьте запрос в [службу поддержки Майкрософт](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online) на увеличение максимального значения для регулирования, указав для этого коммерческое обоснование. Мы проанализируем запрос и в случае положительного решения увеличим максимальное значение для регулирования.