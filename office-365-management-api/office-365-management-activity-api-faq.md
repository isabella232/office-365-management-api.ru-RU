---
ms.TocTitle: Office 365 Management Activity API frequently asked questions
title: 'Вопросы и ответы: API действий управления Office 365'
description: 'Вопросы и ответы: использование API действий управления Office 365'
ms.ContentId: ''
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 9083127d1fd3ecf82e5fe778ba1727d22d91017c
ms.sourcegitcommit: 784b581a699c6d0ab7939ea621d5ecbea71925ea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2019
ms.locfileid: "35924779"
---
# <a name="office-365-management-activity-api-frequently-asked-questions"></a>Вопросы и ответы: API действий управления Office 365

#### <a name="what-events-are-audited-for-a-specific-office-365-service"></a>В случае каких событий проводится аудит для определенной службы Office 365?

В документации по схеме API действий управления Office 365 приведен полный список событий. Дополнительные сведения см. в статье [Схема API действий управления Office 365](office-365-management-activity-api-schema.md). Кроме того, в статье[Поиск по журналу аудита в Центре безопасности и соответствия требованиям](https://docs.microsoft.com/en-us/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#audited-activities) в разделе "Подлежащие аудиту действия" приводится список событий для большинства служб Office 365, которые подлежат аудиту.

#### <a name="how-do-i-onboard-to-the-management-activity-api"></a>Как подключиться к API действий управления?

Сведения о том, как начать работу с API действий управления Office 365, см. в статье [Начало работы с API управления Office 365](get-started-with-office-365-management-apis.md).
 
#### <a name="what-is-the-throttling-limit-for-the--management-activity-api"></a>Каково ограничение на регулирование для API действий управления?

Текущее ограничение для регулирования составляет 60 000 запросов в минуту на идентификатор издателя. 

#### <a name="we-want-to-programmatically-capture-all-events-in-all-workloads-what-is-the-most-reliable-way-to-do-this"></a>Мы хотим программным способом собирать данные обо всех событиях во всех рабочих нагрузках. Как это лучше сделать?

Это можно сделать, используя API действий управления Office 365. Рекомендуем также использовать **модель извлечения**, так как с веб-перехватчиками возникают проблемы. Дополнительные сведения см. в разделе, посвященном использованию веб-перехватчиков, из статьи [Устранение неполадок, связанных с API действий управления Office 365](troubleshooting-the-office-365-management-activity-api.md#using-webhooks).

#### <a name="is-it-true-that-mailbox-auditing-in-exchange-online-can-only-be-enabled-by-using-powershell"></a>Аудит почтовых ящиков в Exchange Online действительно можно включить только с помощью PowerShell?

Так было раньше, но с января 2019 г. аудит почтовых ящиков включен по умолчанию для всех организаций, использующих Office 365. Дополнительные сведения см. в статье [Управление аудитом почтовых ящиков](https://docs.microsoft.com/office365/securitycompliance/enable-mailbox-auditing).

#### <a name="are-there-any-differences-in-the-records-that-are-fetched-by-the-management-activity-api-versus-the-records-that-are-returned-by-using-the-audit-log-search-tool-in-the-office-365-security--compliance-center"></a>Есть ли разница между записями, которые получены API действий управления, и записями, которые возвращены средством поиска в журналах аудита, доступным в Центре безопасности и соответствия требованиям Office 365?

В обоих случаях возвращаются одни и те же данные. Фильтрация не выполняется. Единственное отличие заключается в том, что с помощью API за один подход можно получить данные за последние 7 дней. При поиске в журнале аудита в Центре безопасности и соответствия требованиям (или при использовании соответствующего командлета [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog) в Exchange Online) можно получить данные за последние 90 дней. 

#### <a name="what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api"></a>Что произойдет, если я отключу аудит для своей организации Office 365? Буду ли я по-прежнему получать события через API действий управления?

Нет. Чтобы получать записи через API действий управления, необходимо включить единый аудит Office 365 для своей организации. Инструкции см. в статье [Включение и отключение поиска в журнале аудита Office 365](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).

#### <a name="arent-webhook-notifications-more-immediate-after-all-arent-they-event-driven"></a>Разве использование уведомлений веб-перехватчиков не предполагает более быстрое получение результатов? Они же создаются при появлении событий?

Нет. Уведомления веб-перехватчиков не создаются автоматически сразу после появления событий. Нужно создать большой двоичный объект контента. Такое создание можно считать триггером доставки уведомлений. В последнее время период ожидания, предшествующий получению уведомлений, в случае использования веб-перехватчиков был дольше, чем в случае отправки API запросов непосредственно с помощью операции */content*. API действий управления не стоит рассматривать как систему оповещений о событиях безопасности в режиме реального времени. Корпорация Майкрософт предлагает другие продукты для этого. В случае обеспечения безопасности уведомления о событиях, получаемые с помощью API действий управления, больше подходят для определения тенденций использования за длительные периоды.

#### <a name="when-pulling-the-data-from-the-management-activity-api-there-is-sometimes-a-delay-of-more-than-3-to-5-days-why-is-this"></a>При извлечении данных из API действий управления иногда происходит задержка, длящаяся дольше 3–5 дней. Почему это происходит?

Иногда в службе Office 365 поваляются экземпляры временных сбоев или другие проблемы. В этом случае некоторые записи аудита удаляются, и служба пытается выполнить их обратную засыпку. Хотя такое происходит только с 5–10 % записей, в некоторых ситуациях именно с этими записями может быть связана задержка. Если такая задержка длится более 5 дней, ознакомьтесь с данными на панели мониторинга работоспособности служб в Центре администрирования Office 365. При необходимости также можно отправить запрос в [службу поддержки Майкрософт](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online).

#### <a name="im-encountering-a-throttling-error-in-the-management-activity-api-what-should-i-do"></a>У меня возникла ошибка регулирования в API действий управления. Что делать?

Отправьте запрос в [службу поддержки Майкрософт](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online) на увеличение максимального значения для регулирования, указав для этого коммерческое обоснование. Мы проанализируем запрос и в случае положительного решения увеличим максимальное значение для регулирования.

#### <a name="why-are-targetupdatedproperties-no-longer-in-extendedproperties-in-the-audit-logs-for-azure-active-directory-activities"></a>Почему TargetUpdatedProperties больше не находятся в свойстве ExtendedProperties в журналах аудита для действий Azure Active Directory?

TargetUpdatedProperties отображались в объекте ExtendedProperties. Однако они были удалены из свойства ExtendedProperties и теперь отображаются в свойстве ModifiedProperties.
