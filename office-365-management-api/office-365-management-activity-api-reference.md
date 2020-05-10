---
ms.TocTitle: Office 365 Management Activity API reference
title: Справочник по API действий управления Office 365
description: API действий управления Office 365 используется для получения сведений о событиях и действиях пользователей, администраторов, системы и политик из журналов действий Office 365 и Azure AD.
ms.ContentId: 52749845-37f8-6076-7ea5-49d9a4055445
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 48065e1770e485ffa04778d662a170ae14916354
ms.sourcegitcommit: d55928a0d535090fa2dbe94f38c7316d0e52e9a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "44173143"
---
# <a name="office-365-management-activity-api-reference"></a><span data-ttu-id="bb8c6-103">Справочник по API действий управления Office 365</span><span class="sxs-lookup"><span data-stu-id="bb8c6-103">Office 365 Management Activity API reference</span></span>

<span data-ttu-id="bb8c6-104">API действий управления Office 365 используется для получения сведений о событиях и действиях пользователей, администраторов, системы и политик из журналов действий Office 365 и Azure AD.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-104">Use the Office 365 Management Activity API to retrieve information about user, admin, system, and policy actions and events from Office 365 and Azure AD activity logs.</span></span> 

<span data-ttu-id="bb8c6-105">С помощью действий и событий из журналов аудита и действий Office 365 и Microsoft Azure Active Directory вы можете создавать решения, обеспечивающие мониторинг, анализ и визуализацию данных.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-105">You can use the actions and events from the Office 365 and Microsoft Azure Active Directory audit and activity logs to create solutions that provide monitoring, analysis, and data visualization.</span></span> <span data-ttu-id="bb8c6-106">Эти решения помогают организациям отслеживать действия, выполняемые с их контентом.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-106">These solutions give organizations greater visibility into actions taken on their content.</span></span> <span data-ttu-id="bb8c6-107">Эти действия и события также доступны в отчетах об активности Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-107">These actions and events are also available in the Office 365 Activity Reports.</span></span> <span data-ttu-id="bb8c6-108">Дополнительные сведения см. в статье [Поиск по журналу аудита в Центре безопасности и соответствия требованиям Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-108">For more information, see [Search the audit log in the Office 365 Security & Compliance Center](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).</span></span>

<span data-ttu-id="bb8c6-109">API действий управления Office 365 — это веб-служба REST, с помощью которой можно разрабатывать решения на любом языке и в любой среде внешнего размещения, поддерживающей сертификаты HTTPS и X.509.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-109">The Office 365 Management Activity API is a REST web service that you can use to develop solutions using any language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="bb8c6-110">Этот API использует службу Azure AD и протокол OAuth2 для проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-110">The API relies on Azure AD and the OAuth2 protocol for authentication and authorization.</span></span> <span data-ttu-id="bb8c6-111">Чтобы получить доступ к API из приложения, необходимо сначала зарегистрировать его в Azure AD и настроить подходящие разрешения.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-111">To access the API from your application, you'll need to first register it in Azure AD and configure it with appropriate permissions.</span></span> <span data-ttu-id="bb8c6-112">Благодаря этому приложение сможет запрашивать маркеры доступа OAuth2, необходимые для вызова API.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-112">This will enable your application to request the OAuth2 access tokens it needs to call the API.</span></span> <span data-ttu-id="bb8c6-113">Дополнительные сведения см. в статье [Начало работы с интерфейсами API управления Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-113">For more information, see [Get started with Office 365 Management APIs](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="bb8c6-114">Сведения о данных, которые возвращает API действий управления Office 365, см. в статье [Схема API действий управления Office 365](office-365-management-activity-api-schema.md).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-114">For information about the data that the Office 365 Management Activity API returns, see [Office 365 Management Activity API schema](office-365-management-activity-api-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bb8c6-115">Чтобы получить доступ к данным с помощью API действий управления Office 365, требуется включить ведение единого журнала аудита для организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-115">Before you can access data through the Office 365 Management Activity API, you must enable unified audit logging for your Office 365 organization.</span></span> <span data-ttu-id="bb8c6-116">Это выполняется путем включения журнала аудита Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-116">You do this by turning on the Office 365 audit log.</span></span> <span data-ttu-id="bb8c6-117">Инструкции см. в статье [Включение и отключение поиска в журнале аудита Office 365](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-117">For instructions, see [Turn Office 365 audit log search on or off](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).</span></span>


## <a name="working-with-the-office-365-management-activity-api"></a><span data-ttu-id="bb8c6-118">Работа с API действий управления Office 365</span><span class="sxs-lookup"><span data-stu-id="bb8c6-118">Working with the Office 365 Management Activity API</span></span>

<span data-ttu-id="bb8c6-119">API действий управления Office 365 собирает действия и события в большие двоичные объекты, содержащие контент для определенных клиентов и классифицируемые по типу и источнику контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-119">The Office 365 Management Activity API aggregates actions and events into tenant-specific content blobs, which are classified by the type and source of the content they contain.</span></span> <span data-ttu-id="bb8c6-120">В настоящее время поддерживаются следующие типы контента:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-120">Currently, these content types are supported:</span></span>

- <span data-ttu-id="bb8c6-121">Audit.AzureActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="bb8c6-121">Audit.AzureActiveDirectory</span></span>
    
- <span data-ttu-id="bb8c6-122">Audit.Exchange</span><span class="sxs-lookup"><span data-stu-id="bb8c6-122">Audit.Exchange</span></span>
    
- <span data-ttu-id="bb8c6-123">Audit.SharePoint</span><span class="sxs-lookup"><span data-stu-id="bb8c6-123">Audit.SharePoint</span></span>
    
- <span data-ttu-id="bb8c6-124">Audit.General (включает все остальные рабочие нагрузки, не входящие в предыдущие типы контента)</span><span class="sxs-lookup"><span data-stu-id="bb8c6-124">Audit.General (includes all other workloads not included in the previous content types)</span></span>

- <span data-ttu-id="bb8c6-125">DLP.All (только события DLP для всех рабочих нагрузок)</span><span class="sxs-lookup"><span data-stu-id="bb8c6-125">DLP.All (DLP events only for all workloads)</span></span>
    
<span data-ttu-id="bb8c6-126">Подробные сведения о событиях и свойствах, связанных с этими типами контента, см. в статье [Схема API действий управления Office 365](office-365-management-activity-api-schema.md).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-126">For details about the events and properties associated with these content types, see [Office 365 Management Activity API schema](office-365-management-activity-api-schema.md).</span></span>

<span data-ttu-id="bb8c6-127">Чтобы приступить к получению больших двоичных объектов с контентом для клиента, необходимо сначала создать подписку на нужные типы контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-127">To begin retrieving content blobs for a tenant, you first a create subscription to the desired content types.</span></span> <span data-ttu-id="bb8c6-128">Если вы получаете большие двоичные объекты с контентом для нескольких клиентов, следует создать несколько подписок для каждого из нужных типов контента, по одной на клиент.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-128">If you are retrieving content blobs for multiple tenants, you create multiple subscriptions to each of the desired content types, one for each tenant.</span></span>

<span data-ttu-id="bb8c6-129">Создав подписку, вы можете регулярно проводить опрос для обнаружения новых больших двоичных объектов с контентом, доступных для скачивания. Вы также можете зарегистрировать конечную точку веб-перехватчика с подпиской, чтобы мы отправляли на нее уведомления, когда становятся доступны новые объекты.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-129">After you create a subscription, you can poll regularly to discover new content blobs that are available for download, or you can register a webhook endpoint with the subscription and we will send notifications to this endpoint as new content blobs are available.</span></span>


> [!NOTE] 
> <span data-ttu-id="bb8c6-130">После создания подписки может потребоваться до 12 часов, чтобы для нее стали доступны первые объекты.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-130">When a subscription is created, it can take up to 12 hours for the first content blobs to become available for that subscription.</span></span> <span data-ttu-id="bb8c6-131">Большие двоичные объекты с контентом создаются путем сбора и агрегирования действий и событий с нескольких серверов и центров обработки данных.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-131">The content blobs are created by collecting and aggregating actions and events across multiple servers and datacenters.</span></span> <span data-ttu-id="bb8c6-132">В результате этого распределенного процесса действия и события из больших двоичных объектов не обязательно отображаются в порядке их выполнения.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-132">As a result of this distributed process, the actions and events contained in the content blobs will not necessarily appear in the order in which they occurred.</span></span> <span data-ttu-id="bb8c6-133">Объект может содержать действия и события, произошедшие до действий и событий, содержащихся в ранее обработанном объекте.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-133">One content blob can contain actions and events that occurred prior to the actions and events contained in an earlier content blob.</span></span> <span data-ttu-id="bb8c6-134">Мы работаем над уменьшением задержки между возникновением действий и событий и их появлением в большом двоичном объекте, но не можем гарантировать, что они будут отображаться в хронологическом порядке.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-134">We are working to decrease the latency between the occurrence of actions and events and their availability within a content blob, but we can't guarantee that they appear sequentially.</span></span>


> [!NOTE] 
> <span data-ttu-id="bb8c6-135">Конфиденциальные данные DLP доступны только в API веб-каналов активности для пользователей с разрешениями "Чтение конфиденциальных данных DLP".</span><span class="sxs-lookup"><span data-stu-id="bb8c6-135">DLP sensitive data is only available in the activity feed API to users that have been granted “Read DLP sensitive data” permissions.</span></span> <span data-ttu-id="bb8c6-136">Дополнительные сведения о защите от потери данных (DLP) см. в статье [Обзор политик защиты от потери данных](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)</span><span class="sxs-lookup"><span data-stu-id="bb8c6-136">For more on Data Loss Prevention (DLP) see [Overview of Data Loss Prevention Policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)</span></span>

## <a name="activity-api-operations"></a><span data-ttu-id="bb8c6-137">Операции с API действий</span><span class="sxs-lookup"><span data-stu-id="bb8c6-137">Activity API operations</span></span>

<span data-ttu-id="bb8c6-138">Все операции с API выполняются в рамках одного клиента, а корневой URL-адрес API включает ИД клиента, который задает контекст.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-138">All API operations are scoped to a single tenant and the root URL of the API includes a tenant ID that specifies the tenant context.</span></span> <span data-ttu-id="bb8c6-139">ИД клиента представляет собой GUID.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-139">The tenant ID is a GUID.</span></span> <span data-ttu-id="bb8c6-140">Сведения о том, как получить GUID, см. в статье [Начало работы с интерфейсами API управления Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-140">For information about how to get the GUID, see [Get started with Office 365 Management APIs](get-started-with-office-365-management-apis.md).</span></span> 

<span data-ttu-id="bb8c6-141">Так как уведомления, отправляемые веб-перехватчику, включают ИД клиента, вы можете получать уведомления для всех клиентов с помощью одного веб-перехватчика.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-141">Because the notifications we send to your webhook include the tenant ID, you can use the same webhook to receive notifications for all tenants.</span></span>

<span data-ttu-id="bb8c6-142">URL-адрес конечной точки API зависит от плана подписки на Microsoft 365 или Office 365 для вашей организации.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-142">The URL for the API endpoint that you use is based on the type of Microsoft 365 or Office 365 subscription plan for your organization.</span></span>

<span data-ttu-id="bb8c6-143">**План Enterprise и план для государственных организаций (GCC)**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-143">**Enterprise plan and GCC government plan**</span></span>

```http
https://manage.office.com/api/v1.0/{tenant_id}/activity/feed/{operation}
```

<span data-ttu-id="bb8c6-144">**План для государственных организаций (GCC High)**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-144">**GCC High government plan**</span></span>

```http
https://manage.office365.us/api/v1.0/{tenant_id}/activity/feed/{operation}
```

<span data-ttu-id="bb8c6-145">**План для государственных организаций (DoD)**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-145">**DoD government plan**</span></span>

```http
https://manage.protection.apps.mil/api/v1.0/{tenant_id}/activity/feed/{operation}
```

<span data-ttu-id="bb8c6-146">Для всех операций с API необходим заголовок HTTP Authorization с маркером доступа, полученным из Azure AD.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-146">All API operations require an Authorization HTTP header with an access token obtained from Azure AD.</span></span> <span data-ttu-id="bb8c6-147">ИД клиента в маркере доступа должен совпадать с ИД клиента в корневом URL-адресе API, а маркер доступа должен содержать утверждение ActivityFeed.Read (оно соответствует разрешению [Чтение данных о действиях для организации], настроенному для приложения в Azure AD).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-147">The tenant ID in the access token must match the tenant ID in the root URL of the API and the access token must contain the ActivityFeed.Read claim (this corresponds to the permission [Read activity data for an organization] that you configured for you application in Azure AD).</span></span>

```json
Authorization: Bearer eyJ0e...Qa6wg
```

<span data-ttu-id="bb8c6-148">API действий поддерживает следующие операции:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-148">The Activity API supports the following operations:</span></span>

- <span data-ttu-id="bb8c6-149">**создание подписки** на получение уведомлений и данных об активности для клиента;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-149">**Start a subscription** to begin receiving notifications and retrieving activity data for a tenant.</span></span>
    
- <span data-ttu-id="bb8c6-150">**отмена подписки**, позволяющая перестать получать данные для клиента;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-150">**Stop a subscription** to discontinue retrieving data for a tenant.</span></span>
    
- <span data-ttu-id="bb8c6-151">**вывод списка текущих подписок**;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-151">**List current subscriptions**</span></span>
    
- <span data-ttu-id="bb8c6-152">**вывод списка доступного контента** и соответствующих URL-адресов;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-152">**List available content** and the corresponding content URLs.</span></span>
    
- <span data-ttu-id="bb8c6-153">**получение уведомлений**, отправляемых веб-перехватчиком, когда становится доступен новый контент;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-153">**Receiving notifications** sent by a webhook when new content is available.</span></span>
    
- <span data-ttu-id="bb8c6-154">**получение контента** по URL-адресу;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-154">**Retrieving content** by using the content URL.</span></span>
    
- <span data-ttu-id="bb8c6-155">**вывод списка уведомлений**, отправленных веб-перехватчиком;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-155">**List notifications** sent by a webhook.</span></span>

- <span data-ttu-id="bb8c6-156">**получение понятных имен ресурсов** для объектов в веб-канале данных, указанном идентификаторами GUID.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-156">**Retrieve resource friendly names** for objects in the data feed identified by guids.</span></span>
    

## <a name="start-a-subscription"></a><span data-ttu-id="bb8c6-157">Создание подписки</span><span class="sxs-lookup"><span data-stu-id="bb8c6-157">Start a subscription</span></span>

<span data-ttu-id="bb8c6-158">Эта операция создает подписку на указанный тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-158">This operation starts a subscription to the specified content type.</span></span> <span data-ttu-id="bb8c6-159">Если подписка на указанный тип контента уже существует, эта операция используется для:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-159">If a subscription to the specified content type already exists, this operation is used to:</span></span>

- <span data-ttu-id="bb8c6-160">обновления свойств активного веб-перехватчика;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-160">Update the properties of an active webhook.</span></span>
    
- <span data-ttu-id="bb8c6-161">включения веб-перехватчика, отключенного по причине избыточного количества неудачных попыток отправки уведомления;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-161">Enable a webhook that was disabled because of excessive failed notifications.</span></span>
    
- <span data-ttu-id="bb8c6-162">повторного включения устаревшего веб-перехватчика путем указания более поздней или нулевой конечной даты срока действия;</span><span class="sxs-lookup"><span data-stu-id="bb8c6-162">Re-enable an expired webhook by specifying a later or null expiration date.</span></span>
    
- <span data-ttu-id="bb8c6-163">удаления веб-перехватчика.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-163">Remove a webhook.</span></span>
    
||<span data-ttu-id="bb8c6-164">Подписка</span><span class="sxs-lookup"><span data-stu-id="bb8c6-164">Subscription</span></span>|<span data-ttu-id="bb8c6-165">Описание</span><span class="sxs-lookup"><span data-stu-id="bb8c6-165">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb8c6-166">**Путь**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-166">**Path**</span></span>| `/subscriptions/start?contentType={ContentType}`||
|<span data-ttu-id="bb8c6-167">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-167">**Parameters**</span></span>|<span data-ttu-id="bb8c6-168">contentType</span><span class="sxs-lookup"><span data-stu-id="bb8c6-168">contentType</span></span>|<span data-ttu-id="bb8c6-169">Это должен быть допустимый тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-169">Must be a valid content type.</span></span>|
||<span data-ttu-id="bb8c6-170">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="bb8c6-170">PublisherIdentifier</span></span>|<span data-ttu-id="bb8c6-171">GUID клиента поставщика, который обращается к API из кода.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-171">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="bb8c6-172">Это **не** GUID приложения или пользователя, работающего с приложением, а GUID компании, написавшей код.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-172">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="bb8c6-173">Этот параметр используется для регулирования частоты запросов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-173">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="bb8c6-174">Убедитесь, что этот параметр указан во всех отправляемых запросах, чтобы получить отдельную квоту.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-174">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="bb8c6-175">Ко всем полученным запросам без этого параметра применяется одна квота.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-175">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="bb8c6-176">**Основной текст**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-176">**Body**</span></span>|<span data-ttu-id="bb8c6-177">webhook</span><span class="sxs-lookup"><span data-stu-id="bb8c6-177">webhook</span></span>|<span data-ttu-id="bb8c6-178">Необязательный объект JSON с тремя свойствами:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-178">Optional JSON object with three properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-179"><b>address.</b> Обязательная конечная точка HTTPS, которая может получать уведомления.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-179"><b>address</b>: Required HTTPS endpoint that can receive notifications.</span></span>  <span data-ttu-id="bb8c6-180">Веб-перехватчику будет отправлено тестовое сообщение для его проверки без создания подписки.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-180">A test message will be sent to the webhook to validate the webhook before creating the subscription.</span></span></p></li><li><p><span data-ttu-id="bb8c6-181"><b>authId.</b> Необязательная строка, которая будет включаться в качестве заголовка WebHook-AuthID в уведомления, отправляемые веб-перехватчику, чтобы идентифицировать и авторизовать источник запроса к нему.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-181"><b>authId</b>: Optional string that will be included as the WebHook-AuthID header in notifications sent to the webhook as a means of identifying and authorizing the source of the request to the webhook.</span></span></p></li><li><p><span data-ttu-id="bb8c6-182"><b>expiration.</b> Необязательные дата и время, после которых веб-перехватчику больше не следует отправлять уведомления.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-182"><b>expiration</b>: Optional datetime that indicates a datetime after which notifications should no longer be sent to the webhook.</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-183">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-183">**Response**</span></span>|<span data-ttu-id="bb8c6-184">contentType</span><span class="sxs-lookup"><span data-stu-id="bb8c6-184">contentType</span></span>|<span data-ttu-id="bb8c6-185">Тип контента, указанный в вызове.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-185">The content type specified in the call.</span></span>|
||<span data-ttu-id="bb8c6-186">status</span><span class="sxs-lookup"><span data-stu-id="bb8c6-186">status</span></span>|<span data-ttu-id="bb8c6-187">Состояние подписки.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-187">The status of the subscription.</span></span> <span data-ttu-id="bb8c6-188">Если подписка отключена, перечислять и получать контент будет невозможно.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-188">If a subscription is disabled, you will not be able to list or retrieve content.</span></span>|
||<span data-ttu-id="bb8c6-189">webhook</span><span class="sxs-lookup"><span data-stu-id="bb8c6-189">webhook</span></span>|<span data-ttu-id="bb8c6-190">Свойства веб-перехватчика, указанные в вызове вместе с его состоянием.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-190">The webhook properties specified in the call together with the status of the webhook.</span></span> <span data-ttu-id="bb8c6-191">Если веб-перехватчик отключен, вы не будете получать уведомления, но по-прежнему сможете перечислять и получать контент, при условии что подписка включена.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-191">If the webhook is disabled, you will not receive notification, but you will still be able to list and retrieve content, provided the subscription is enabled.</span></span>|

#### <a name="sample-request"></a><span data-ttu-id="bb8c6-192">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-192">Sample request</span></span>

```json
POST {root}/subscriptions/start?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Content-Type: application/json; utf-8
Authorization: Bearer eyJ0e...Qa6wg

{
    "webhook" : {
        "address": "https://webhook.myapp.com/o365/",
        "authId": "o365activityapinotification",
        "expiration": ""
    }
}

```


#### <a name="sample-response"></a><span data-ttu-id="bb8c6-193">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-193">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
    "contentType": "Audit.SharePoint",
    "status": "enabled",
    "webhook": {
        "status": "enabled",
        "address":  "https://webhook.myapp.com/o365/",
        "authId": "o365activityapinotification",
        "expiration": null
    }
}

```


## <a name="webhook-validation"></a><span data-ttu-id="bb8c6-194">Проверка веб-перехватчиков</span><span class="sxs-lookup"><span data-stu-id="bb8c6-194">Webhook validation</span></span>

<span data-ttu-id="bb8c6-195">При вызове операции /start с указанием веб-перехватчика мы отправим уведомление о проверке на указанный адрес веб-перехватчика, чтобы убедиться, что активный прослушиватель может принимать и обрабатывать уведомления.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-195">When the /start operation is called and a webhook is specified, we will send a validation notification to the specified webhook address to validate that an active listener can accept and process notifications.</span></span> <span data-ttu-id="bb8c6-196">Если мы не получим отклик HTTP 200 OK, подписка не будет создана.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-196">If we do not receive an HTTP 200 OK response, the subscription will not be created.</span></span> <span data-ttu-id="bb8c6-197">Если же операция /start вызывается для добавления веб-перехватчика к имеющейся подписке, а отклик HTTP 200 OK не получен, то веб-перехватчик не будет добавлен, а подписка останется без изменений.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-197">Or, if /start is being called to add a webhook to an existing subscription and a response of HTTP 200 OK is not received, the webhook will not be added and the subscription will remain unchanged.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="bb8c6-198">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-198">Sample request</span></span>

```json
POST {webhook address}
Content-Type: application/json; charset=utf-8
Webhook-AuthID: (webhook authId, if provided)
Webhook-ValidationCode: (random opaque string)

{
    "validationCode": (random opaque string, same as header)
}

```


#### <a name="sample-response"></a><span data-ttu-id="bb8c6-199">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-199">Sample response</span></span>

```json

HTTP/1.1 200 OK

```


## <a name="stop-a-subscription"></a><span data-ttu-id="bb8c6-200">Остановка подписки</span><span class="sxs-lookup"><span data-stu-id="bb8c6-200">Stop a subscription</span></span>

<span data-ttu-id="bb8c6-201">Эта операция отменяет подписку на указанный тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-201">This operation stops a subscription to the specified content type.</span></span> 

<span data-ttu-id="bb8c6-202">После отмены подписки вы больше не будете получать уведомления, а извлекать доступный контент будет невозможно.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-202">When a subscription is stopped, you will no longer receive notifications and you will not be able to retrieve available content.</span></span> <span data-ttu-id="bb8c6-203">Заново оформив подписку, вы получите доступ к новому контенту с этого момента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-203">If the subscription is later restarted, you will have access to new content from that point forward.</span></span> <span data-ttu-id="bb8c6-204">Получать контент, который был доступен с момента отмены подписки до ее повторного создания, будет невозможно.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-204">You will not be able to retrieve content that was available between the time the subscription was stopped and restarted.</span></span>


||<span data-ttu-id="bb8c6-205">Подписка</span><span class="sxs-lookup"><span data-stu-id="bb8c6-205">Subscription</span></span>|<span data-ttu-id="bb8c6-206">Описание</span><span class="sxs-lookup"><span data-stu-id="bb8c6-206">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb8c6-207">**Путь**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-207">**Path**</span></span>| `/subscriptions/stop?contentType={ContentType}`||
|<span data-ttu-id="bb8c6-208">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-208">**Parameters**</span></span>|<span data-ttu-id="bb8c6-209">contentType</span><span class="sxs-lookup"><span data-stu-id="bb8c6-209">contentType</span></span>|<span data-ttu-id="bb8c6-210">Это должен быть допустимый тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-210">Must be a valid content type.</span></span>|
||<span data-ttu-id="bb8c6-211">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="bb8c6-211">PublisherIdentifier</span></span>|<span data-ttu-id="bb8c6-212">GUID клиента поставщика, который обращается к API из кода.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-212">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="bb8c6-213">Это **не** GUID приложения или пользователя, работающего с приложением, а GUID компании, написавшей код.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-213">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="bb8c6-214">Этот параметр используется для регулирования частоты запросов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-214">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="bb8c6-215">Убедитесь, что этот параметр указан во всех отправляемых запросах, чтобы получить отдельную квоту.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-215">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="bb8c6-216">Ко всем полученным запросам без этого параметра применяется одна квота.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-216">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="bb8c6-217">**Основной текст**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-217">**Body**</span></span>|<span data-ttu-id="bb8c6-218">(пусто)</span><span class="sxs-lookup"><span data-stu-id="bb8c6-218">(empty)</span></span>||
|<span data-ttu-id="bb8c6-219">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-219">**Response**</span></span>|<span data-ttu-id="bb8c6-220">(пусто)</span><span class="sxs-lookup"><span data-stu-id="bb8c6-220">(empty)</span></span>|||

#### <a name="sample-request"></a><span data-ttu-id="bb8c6-221">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-221">Sample request</span></span>

```json
POST {root}/subscriptions/stop?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="bb8c6-222">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-222">Sample response</span></span>

```json
HTTP/1.1 200 OK
```


## <a name="list-current-subscriptions"></a><span data-ttu-id="bb8c6-223">Вывод списка текущих подписок</span><span class="sxs-lookup"><span data-stu-id="bb8c6-223">List current subscriptions</span></span>

<span data-ttu-id="bb8c6-224">Эта операция возвращает коллекцию текущих подписок вместе со связанными веб-перехватчиками.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-224">This operation returns a collection of the current subscriptions together with the associated webhooks.</span></span>

||<span data-ttu-id="bb8c6-225">Подписка</span><span class="sxs-lookup"><span data-stu-id="bb8c6-225">Subscription</span></span>|<span data-ttu-id="bb8c6-226">Описание</span><span class="sxs-lookup"><span data-stu-id="bb8c6-226">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb8c6-227">**Путь**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-227">**Path**</span></span>| `/subscriptions/list`||
|<span data-ttu-id="bb8c6-228">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-228">**Parameters**</span></span>|<span data-ttu-id="bb8c6-229">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="bb8c6-229">PublisherIdentifier</span></span>|<span data-ttu-id="bb8c6-230">GUID клиента поставщика, который обращается к API из кода.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-230">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="bb8c6-231">Это **не** GUID приложения или пользователя, работающего с приложением, а GUID компании, написавшей код.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-231">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="bb8c6-232">Этот параметр используется для регулирования частоты запросов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-232">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="bb8c6-233">Убедитесь, что этот параметр указан во всех отправляемых запросах, чтобы получить отдельную квоту.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-233">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="bb8c6-234">Ко всем полученным запросам без этого параметра применяется одна квота.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-234">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="bb8c6-235">**Основной текст**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-235">**Body**</span></span>|<span data-ttu-id="bb8c6-236">(пусто)</span><span class="sxs-lookup"><span data-stu-id="bb8c6-236">(empty)</span></span>||
|<span data-ttu-id="bb8c6-237">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-237">**Response**</span></span>|<span data-ttu-id="bb8c6-238">Массив JSON</span><span class="sxs-lookup"><span data-stu-id="bb8c6-238">JSON array</span></span>|<span data-ttu-id="bb8c6-239">Каждая подписка будет представлена объектом JSON с тремя свойствами:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-239">Each subscription will be represented by a JSON object with three properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-240"><b>contentType.</b> Указывает тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-240"><b>contentType</b>: Indicates the content type.</span></span></p></li><li><p><span data-ttu-id="bb8c6-241"><b>status.</b> Указывает состояние подписки.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-241"><b>status</b>: Indicates the status of the subscription.</span></span></p></li><li><p><span data-ttu-id="bb8c6-242"><b>webhook.</b> Указывает настроенный веб-перехватчик, а также его состояние (включен, отключен, устарел).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-242"><b>webhook</b>: Indicates the configured webhook, together with the status (enabled, disabled, expired) of the webhook.</span></span>  <span data-ttu-id="bb8c6-243">Если у подписки нет веб-перехватчика, то для свойства webhook будет задано значение null.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-243">If a subscription does not have a webhook, the webhook property will be present but with null value.</span></span></p></li></ul>|


#### <a name="sample-request"></a><span data-ttu-id="bb8c6-244">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-244">Sample request</span></span>

```json
GET {root}/subscriptions/list?PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="bb8c6-245">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-245">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "contentType" : "Audit.SharePoint",
        "status": "enabled",
        "webhook": {
            "status": "enabled",
            "address": "https://webhook.myapp.com/o365/",
            "authId": "o365activityapinotification",
            "expiration": null
        }
    },

    ...

    {
        "contentType": "Audit.Exchange",
        "webhook": null
    }
]

```


## <a name="list-available-content"></a><span data-ttu-id="bb8c6-246">Вывод списка доступного контента</span><span class="sxs-lookup"><span data-stu-id="bb8c6-246">List available content</span></span>

<span data-ttu-id="bb8c6-247">Эта операция перечисляет контент указанного типа, доступный в данный момент для получения.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-247">This operation lists the content currently available for retrieval for the specified content type.</span></span> <span data-ttu-id="bb8c6-248">Этот контент представляет собой сочетание действий и событий, полученных с нескольких серверов из нескольких центров обработки данных.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-248">The content is an aggregation of actions and events harvested from multiple servers across multiple datacenters.</span></span> <span data-ttu-id="bb8c6-249">Список контента упорядочен по времени появления сборок, но события и действия в рамках этих сборок не обязательно будут указаны по порядку.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-249">The content will be listed in the order in which the aggregations become available, but the events and actions within the aggregations are not guaranteed to be sequential.</span></span> <span data-ttu-id="bb8c6-250">Если подписка отключена, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-250">An error is returned if the subscription status is disabled.</span></span>


||<span data-ttu-id="bb8c6-251">Подписка</span><span class="sxs-lookup"><span data-stu-id="bb8c6-251">Subscription</span></span>|<span data-ttu-id="bb8c6-252">Описание</span><span class="sxs-lookup"><span data-stu-id="bb8c6-252">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb8c6-253">**Путь**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-253">**Path**</span></span>| `/subscriptions/content?contentType={ContentType}&amp;startTime={0}&amp;endTime={1}`||
|<span data-ttu-id="bb8c6-254">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-254">**Parameters**</span></span>|<span data-ttu-id="bb8c6-255">contentType</span><span class="sxs-lookup"><span data-stu-id="bb8c6-255">contentType</span></span>|<span data-ttu-id="bb8c6-256">Это должен быть допустимый тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-256">Must be a valid content type.</span></span>|
||<span data-ttu-id="bb8c6-257">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="bb8c6-257">PublisherIdentifier</span></span>|<span data-ttu-id="bb8c6-258">GUID клиента поставщика, который обращается к API из кода.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-258">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="bb8c6-259">Это **не** GUID приложения или пользователя, работающего с приложением, а GUID компании, написавшей код.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-259">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="bb8c6-260">Этот параметр используется для регулирования частоты запросов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-260">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="bb8c6-261">Убедитесь, что этот параметр указан во всех отправляемых запросах, чтобы получить отдельную квоту.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-261">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="bb8c6-262">Ко всем полученным запросам без этого параметра применяется одна квота.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-262">All requests received without this parameter will share the same quota.</span></span>|
||<span data-ttu-id="bb8c6-263">startTime endTime</span><span class="sxs-lookup"><span data-stu-id="bb8c6-263">startTime endTime</span></span>|<span data-ttu-id="bb8c6-264">Необязательные значения даты и времени (в формате UTC), указывающие диапазон времени появления возвращаемого контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-264">Optional datetimes (UTC) indicating the time range of content to return, based on when the content became available.</span></span> <span data-ttu-id="bb8c6-265">Диапазон времени включает значение startTime (startTime <= contentCreated), но не включает значение endTime (contentCreated < endTime), что позволяет просматривать доступный контент по непересекающимся последовательным интервалам времени.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-265">The time range is inclusive with respect to startTime (startTime <= contentCreated) and exclusive with respect to endTime (contentCreated < endTime), so that non-overlapping, incrementing time intervals can used to page through available content.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-266">ГГГГ-ММ-ДД</span><span class="sxs-lookup"><span data-stu-id="bb8c6-266">YYYY-MM-DD</span></span></p></li><li><p><span data-ttu-id="bb8c6-267">ГГГГ-ММ-ДДТЧЧ:ММ</span><span class="sxs-lookup"><span data-stu-id="bb8c6-267">YYYY-MM-DDTHH:MM</span></span></p></li><li><p><span data-ttu-id="bb8c6-268">ГГГГ-ММ-ДДТЧЧ:ММ:СС</span><span class="sxs-lookup"><span data-stu-id="bb8c6-268">YYYY-MM-DDTHH:MM:SS</span></span></p></li></ul><span data-ttu-id="bb8c6-269">Необходимо указать оба значения (или пропустить оба значения), а интервал между ними не должен превышать 24 часа. При этом со времени начала должно пройти не более 7 дней.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-269">Both must be specified (or both omitted) and they must be no more than 24 hours apart, with the start time no more than 7 days in the past.</span></span> <span data-ttu-id="bb8c6-270">По умолчанию, если пропустить значения startTime и endTime, возвращается контент, появившийся за последние 24 часа.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-270">By default, if startTime and endTime are omitted, then the content available in the last 24 hours is returned.</span></span><p><span data-ttu-id="bb8c6-271">**ПРИМЕЧАНИЕ**. Вы можете указать значения startTime и endTime с интервалом более 24 часов, но это не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-271">**NOTE**: Even though it is possible to specify a startTime and endTime more than 24 hours apart, this is not recommended.</span></span> <span data-ttu-id="bb8c6-272">Более того, даже если вы получите какие-либо результаты по запросу на период времени продолжительностью более 24 часов, они будут частичными и их не следует учитывать.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-272">Furthermore, if you do get any results in response to a request for more than 24 hours, these could be partial results and should not be taken into account.</span></span> <span data-ttu-id="bb8c6-273">Запрос должен отправляться с интервалом не более 24 часов между значениями startTime и endTime.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-273">The request should be issued with an interval of no more than 24 hours between the startTime and endTime.</span></span></p>|
|<span data-ttu-id="bb8c6-274">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-274">**Response**</span></span>|<span data-ttu-id="bb8c6-275">Массив JSON</span><span class="sxs-lookup"><span data-stu-id="bb8c6-275">JSON array</span></span>|<span data-ttu-id="bb8c6-276">Доступный контент будет представлен объектами JSON со следующими свойствами:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-276">The available content will be represented by JSON objects with the following properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-277"><b>contentType.</b> Указывает тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-277"><b>contentType</b>: Indicates the content type.</span></span></p></li><li><p><span data-ttu-id="bb8c6-278"><b>contentId.</b> Непрозрачная строка, однозначно определяющая контент.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-278"><b>contentId</b>: An opaque string that uniquely identifies the content.</span></span></p></li><li><p><span data-ttu-id="bb8c6-279"><b>contentUri.</b> URL-адрес, используемый при получении контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-279"><b>contentUri</b>: The URL to use when retrieving the content.</span></span></p></li><li><p><span data-ttu-id="bb8c6-280"><b>contentCreated.</b> Дата и время появления контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-280"><b>contentCreated</b>: The datetime when the content was made available.</span></span></p></li><li><p><span data-ttu-id="bb8c6-281"><b>contentExpiration.</b> Дата и время, после которых контент больше не будет доступен для получения.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-281"><b>contentExpiration</b>: The datetime after which the content will no longer be available for retrieval.</span></span></p></li></ul>|


#### <a name="sample-request"></a><span data-ttu-id="bb8c6-282">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-282">Sample request</span></span>

```json
GET {root}/subscriptions/content?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="bb8c6-283">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-283">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "contentType": "Audit.SharePoint",
        "contentId": "492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentUri": "https://manage.office.com/api/v1.0/f28ab78a-d401-4060-8012-736e373933eb/activity/feed/audit/492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentCreated": "2015-05-23T17:35:00.000Z",
        "contentExpiration": "2015-05-30T17:35:00.000Z"
    },
    ...
]

```


### <a name="pagination"></a><span data-ttu-id="bb8c6-284">Разбивка на страницы</span><span class="sxs-lookup"><span data-stu-id="bb8c6-284">Pagination</span></span>

<span data-ttu-id="bb8c6-285">При выводе списка доступного контента за определенный диапазон времени количество возвращаемых результатов ограничено во избежание просроченных откликов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-285">When listing available content for a time range, the number of results returned is limited to prevent response timeouts.</span></span> <span data-ttu-id="bb8c6-286">Если за указанный диапазон времени возвращается больше результатов, чем помещается в один отклик, то результаты будут усечены, а к отклику будет добавлен заголовок с URL-адресом для получения следующей страницы результатов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-286">If there are more results in the specified time range than can be returned in single response, the results will be truncated and a header will be added to the response indicating the URL to use to retrieve the next page of results.</span></span> <span data-ttu-id="bb8c6-287">URL-адрес будет содержать те же параметры _startTime_ и _endTime_, которые были указаны в исходном запросе, вместе с параметрами, указывающими внутренний ИД следующей страницы.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-287">The URL will contain the same  _startTime_ and _endTime_ parameters that were specified in the original request, together with a parameter indicating the internal ID of the next page.</span></span> <span data-ttu-id="bb8c6-288">Если значения _startTime_ и _endTime_ не были указаны в исходном запросе, то будут заданы даты для 24-часового интервала, предшествующего первоначальному запросу.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-288">If _startTime_ and _endTime_ were not specified in the original request, they will be set to reflect the 24-hour interval that preceded the original request.</span></span>


```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
NextPageUri: https://manage.office.com/api/v1/{tenant_id}/activity/feed/subscriptions/content?contentType=Audit.SharePoint&amp;startTime=2015-10-01&amp;endTime=2015-10-02&amp;nextPage=2015101900R022885001761

```

<span data-ttu-id="bb8c6-289">Чтобы получить список доступного контента за указанный диапазон времени, вы можете извлекать страницы, пока не будет получен отклик без заголовка **NextPageUri**.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-289">To list all available content for a specified time range, you might need to retrieve multiple pages until a response without the **NextPageUri** header is received.</span></span>


## <a name="receiving-notifications"></a><span data-ttu-id="bb8c6-290">Получение уведомлений</span><span class="sxs-lookup"><span data-stu-id="bb8c6-290">Receiving notifications</span></span>

<span data-ttu-id="bb8c6-291">По мере появления нового контента веб-перехватчику, настроенному для подписки, отправляются уведомления.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-291">Notifications are sent to the configured webhook for a subscription as new content becomes available.</span></span> <span data-ttu-id="bb8c6-292">Так как уведомление включает идентификатор клиента, вы можете использовать один и тот же веб-перехватчик для получения уведомлений обо всех клиентах, подписки на которые у вас есть.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-292">Because the notification includes the tenant identifier, you can use the same webhook to receive notifications for all tenants for which you have subscriptions.</span></span>

<span data-ttu-id="bb8c6-293">Уведомление содержит запрос HTTP POST по протоколу TLS (TLS 1.0 и более поздних версий) по указанному адресу веб-перехватчика.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-293">The notification is made as an HTTP POST over TLS (TLS 1.0 and later versions) to the specified webhook address.</span></span> <span data-ttu-id="bb8c6-294">Если конфигурация веб-перехватчика включает ИД аутентификации, мы отправим его в качестве HTTP-заголовка Webhook-AuthID.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-294">If the webhook configuration includes an auth ID, we will send it as an HTTP header: Webhook-AuthID.</span></span> <span data-ttu-id="bb8c6-295">Любой отклик, кроме HTTP 200 OK, считается сбоем, и выполняется повторная попытка.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-295">Any response other than HTTP 200 OK will be considered a failure and the notification will be retried.</span></span> <span data-ttu-id="bb8c6-296">Вы также можете настроить веб-перехватчик, чтобы требовалась проверка подлинности на основе клиентских сертификатов, и мы выполним аутентификацию с помощью сертификата manage.office.com.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-296">You can also configure your webhook to require client certificate-based authentication and we will authenticate using the manage.office.com certificate.</span></span>

<span data-ttu-id="bb8c6-297">Текст запроса будет содержать массив из одного или нескольких объектов JSON, представляющих доступные большие двоичные объекты с контентом.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-297">The body of the request will contain an array of one or more JSON objects that represent the available content blobs.</span></span> <span data-ttu-id="bb8c6-298">Количество объектов с контентом в каждом уведомлении ограничено, чтобы размер уведомлений оставался относительно небольшим.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-298">The number of content blobs in each notification is limited to keep the size of the notification relatively small.</span></span> <span data-ttu-id="bb8c6-299">Так как это ограничение может измениться, ваша реализация должна запрашивать длину массива, а не рассчитывать на фиксированный размер.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-299">Because this limit might change, your implementation should query for the length of the array instead of expecting a fixed size.</span></span> <span data-ttu-id="bb8c6-300">Каждый объект будет включать те же свойства, которые возвращает операция /content, а также GUID клиента, которому принадлежат данные, и GUID приложения, создавшего подписки.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-300">Each object will include the same properties returned by the /content operation, together with the GUID of the tenant to which the data belongs and the GUID of your application that created the subscriptions.</span></span> <span data-ttu-id="bb8c6-301">Это позволит веб-перехватчику задать контекст при использовании с несколькими клиентами и приложениями.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-301">This allows the webhook to establish context when it is being used with multiple tenants and applications.</span></span>

- <span data-ttu-id="bb8c6-302">**tenantId.** GUID клиента, которому принадлежит контент.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-302">**tenantId**: The GUID of the tenant to which the content belongs.</span></span>
    
- <span data-ttu-id="bb8c6-303">**clientId.** GUID приложения, создавшего подписку.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-303">**clientId**: The GUID of your application that created the subscription.</span></span>
    
- <span data-ttu-id="bb8c6-304">**contentType.** Указывает тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-304">**contentType**: Indicates the content type.</span></span>
    
- <span data-ttu-id="bb8c6-305">**contentId.** Непрозрачная строка, однозначно определяющая контент.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-305">**contentId**: An opaque string that uniquely identifies the content.</span></span>
    
- <span data-ttu-id="bb8c6-306">**contentUri.** URL-адрес, используемый при получении контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-306">**contentUri**: The URL to use when retrieving the content.</span></span>
    
- <span data-ttu-id="bb8c6-307">**contentCreated.** Дата и время появления контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-307">**contentCreated**: The datetime when the content was made available.</span></span>
    
- <span data-ttu-id="bb8c6-308">**contentExpiration.** Дата и время, после которых контент больше не будет доступен для получения.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-308">**contentExpiration**: The datetime after which the content will no longer be available for retrieval.</span></span>
    
<span data-ttu-id="bb8c6-309">Ниже приводится пример уведомления.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-309">The following is an example of a notification.</span></span>

```json
POST https://webhook.myapp.com/o365/ 
Content-Type: application/json; utf-8
Webhook-AuthID: o365activityapinotification

[
    {
        "tenantId": "{GUID}"
        "clientId": "{GUID}"
        "contentType": "Audit.SharePoint",
        "contentId": "492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentUri": "https://manage.office.com/api/v1.0/f28ab78a-d401-4060-8012-736e373933eb/activity/feed/audit/492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentCreated": "2015-05-23T17:35:00.000Z",
        "contentExpiration": "2015-05-30T17:35:00.000Z"
    },
    ...
]

```


## <a name="notification-failure-and-retry"></a><span data-ttu-id="bb8c6-310">Сбой и повторная попытка отправки уведомления</span><span class="sxs-lookup"><span data-stu-id="bb8c6-310">Notification failure and retry</span></span>

<span data-ttu-id="bb8c6-311">Система уведомлений отправляет уведомления по мере появления нового контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-311">The notification system sends notifications as new content becomes available.</span></span> <span data-ttu-id="bb8c6-312">Если при отправке уведомлений возникнет слишком большое количество сбоев, наш механизм повторных попыток будет экспоненциально увеличивать интервал между попытками.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-312">If we encounter excessive failures when sending notifications, our retry mechanism will exponentially increase the time between retries.</span></span> <span data-ttu-id="bb8c6-313">Если сбои продолжат возникать, мы оставляем за собой право отключить веб-перехватчик и совсем перестать отправлять ему уведомления.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-313">If we continue to encounter failures, we reserve the right to disable the webhook and stop sending notifications to it altogether.</span></span> <span data-ttu-id="bb8c6-314">С помощью операции /start можно заново включить отключенный веб-перехватчик.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-314">The /start operation can be used to re-enable a disabled webhook.</span></span>


## <a name="retrieving-content"></a><span data-ttu-id="bb8c6-315">Получение контента</span><span class="sxs-lookup"><span data-stu-id="bb8c6-315">Retrieving content</span></span>

<span data-ttu-id="bb8c6-316">Чтобы получить большой двоичный объект с контентом, отправьте запрос GET на соответствующий URI, включенный в список доступного контента, и в уведомления, отправляемые веб-перехватчику.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-316">To retrieve a content blob, make a GET request against the corresponding content URI that is included in the list of available content and in the notifications sent to a webhook.</span></span> <span data-ttu-id="bb8c6-317">Возвращаемый контент будет коллекцией из одного или нескольких действий или событий в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-317">The returned content will be a collection of one more actions or events in JSON format.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="bb8c6-318">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-318">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/41463f53-8812-40f4-890f-865bf6e35190/activity/feed/audit/301299007231$301299007231$41463f53881240f4890f865bf6e35190aad2015062920$e1c2ab19858a469fb1f1fd097effffc9$04 HTTP/1.1
Authorization: Bearer eyJ0e...Qa6wg
```

#### <a name="sample-response"></a><span data-ttu-id="bb8c6-319">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-319">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "CreationTime": "2015-06-29T20:03:19",
        "Id": "80c76bd2-9d81-4c57-a97a-accfc3443dca",
        "Operation": "PasswordLogonInitialAuthUsingPassword",
        "OrganizationId": "41463f53-8812-40f4-890f-865bf6e35190",
        "RecordType": 9,
        "ResultStatus": "failed",
        "UserKey": "1153977025279851686@contoso.onmicrosoft.com",
        "UserType": 0,
        "Workload": "AzureActiveDirectory",
        "ClientIP": "134.170.188.221",
        "ObjectId": "admin@contoso.onmicrosoft.com",
        "UserId": "admin@contoso.onmicrosoft.com",
        "AzureActiveDirectoryEventType": 0,
        "ExtendedProperties": [
            {
                "Name": "LoginError",
                "Value": "-2147217390;PP_E_BAD_PASSWORD;The entered and stored passwords do not match."
            }
        ],
        "Client": "Exchange",
        "LoginStatus": -2147217390,
        "UserDomain": "contoso.onmicrosoft.com"
    },
    {
        "CreationTime": "2015-06-29T20:03:34",
        "Id": "4e655d3f-35fa-42e0-b050-264b2d255c7a",
        "Operation": "PasswordLogonInitialAuthUsingPassword",
        "OrganizationId": "41463f53-8812-40f4-890f-865bf6e35190",
        "RecordType": 9,
        "ResultStatus": "success",
        "UserKey": "1153977025279851686@contoso.onmicrosoft.com",
        "UserType": 0,
        "Workload": "AzureActiveDirectory",
        "ClientIP": "134.170.188.221",
        "ObjectId": "admin@contoso.onmicrosoft.com",
        "UserId": "admin@contoso.onmicrosoft.com",
        "AzureActiveDirectoryEventType": 0,
        "Client": "Exchange",
        "LoginStatus": 0,
        "UserDomain": "contoso.onmicrosoft.com"
    },
    {
        "CreationTime": "2015-06-29T20:04:55",
        "Id": "b567caf0-088e-4c1c-a4ea-633a1e3d66c8",
        "Operation": "Add User.",
        "OrganizationId": "41463f53-8812-40f4-890f-865bf6e35190",
        "RecordType": 8,
        "ResultStatus": "success",
        "UserKey": "1003BFFD8EC47CA6@contoso.onmicrosoft.com",
        "UserType": 0,
        "Workload": "AzureActiveDirectory",
        "ObjectId": "user001@contoso.onmicrosoft.com",
        "UserId": "admin@contoso.onmicrosoft.com",
        "AzureActiveDirectoryEventType": 0,
        "Actor": [
            {
                "ID": "1cef1fdb-ff52-48c4-8e4e-dfb5ea83d357",
                "Type": 2
            },
            {
                "ID": "admin@contoso.onmicrosoft.com",
                "Type": 5
            },
            {
                "ID": "1003BFFD8EC47CA6",
                "Type": 3
            }
        ],
        "ActorContextId": "41463f53-8812-40f4-890f-865bf6e35190",
        "InterSystemsId": "c2ced078-ad57-4079-a743-5c37f5284790",
        "IntraSystemId": "d1497f7e-15b4-49aa-83ad-11a17ca4a2f4",
        "Target": [
            {
                "ID": "user001@contoso.onmicrosoft.com",
                "Type": 5
            },
            {
                "ID": "10037FFE91510806",
                "Type": 3
            }
        ],
        "TargetContextId": "41463f53-8812-40f4-890f-865bf6e35190"
    }
]

```


## <a name="list-notifications"></a><span data-ttu-id="bb8c6-320">Список уведомлений</span><span class="sxs-lookup"><span data-stu-id="bb8c6-320">List notifications</span></span>

<span data-ttu-id="bb8c6-321">Эта операция выводит список всех попыток отправки уведомлений об указанном типе контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-321">This operation lists all notification attempts for the specified content type.</span></span> <span data-ttu-id="bb8c6-322">Если вы не включили веб-перехватчик при создании подписки на тип контента, то для получения не будет доступно никаких уведомлений.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-322">If you did not include a webhook when starting the subscription to the content type, there will be no notifications to retrieve.</span></span> <span data-ttu-id="bb8c6-323">Так как мы повторяем попытку отправки уведомления в случае сбоя, эта операция может возвращать множество уведомлений для одного и того же контента, а порядок отправки уведомлений не обязательно будет совпадать с порядком его появления (особенно если происходили сбои и повторные попытки).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-323">Because we retry notifications in the event of failure, this operation can return multiple notifications for the same content, and the order in which the notifications are sent will not necessarily match the order in which the content became available (especially when there are failures and retries).</span></span> 

<span data-ttu-id="bb8c6-324">С помощью этой операции можно расследовать проблемы, связанные с веб-перехватчиками и уведомлениями, но ее не следует использовать для определения контента, доступного для получения в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-324">You can use this operation to help investigate issues related to webhooks and notifications, but you should not use it to determine what content is currently available for retrieval.</span></span> <span data-ttu-id="bb8c6-325">Используйте вместо нее операцию /content.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-325">Use the /content operation instead.</span></span> <span data-ttu-id="bb8c6-326">Мы возвращаем ошибку, если подписка отключена.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-326">We return an error if the subscription status is disabled.</span></span>


||<span data-ttu-id="bb8c6-327">Подписка</span><span class="sxs-lookup"><span data-stu-id="bb8c6-327">Subscription</span></span>|<span data-ttu-id="bb8c6-328">Описание</span><span class="sxs-lookup"><span data-stu-id="bb8c6-328">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb8c6-329">**Путь**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-329">**Path**</span></span>| `/subscriptions/notifications?contentType={ContentType}&amp;startTime={0}&amp;endTime={1}`||
|<span data-ttu-id="bb8c6-330">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-330">**Parameters**</span></span>|<span data-ttu-id="bb8c6-331">contentType</span><span class="sxs-lookup"><span data-stu-id="bb8c6-331">contentType</span></span>|<span data-ttu-id="bb8c6-332">Это должен быть допустимый тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-332">Must be a valid content type.</span></span>|
||<span data-ttu-id="bb8c6-333">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="bb8c6-333">PublisherIdentifier</span></span>|<span data-ttu-id="bb8c6-334">GUID клиента поставщика, который обращается к API из кода.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-334">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="bb8c6-335">Это **не** GUID приложения или пользователя, работающего с приложением, а GUID компании, написавшей код.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-335">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="bb8c6-336">Этот параметр используется для регулирования частоты запросов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-336">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="bb8c6-337">Убедитесь, что этот параметр указан во всех отправляемых запросах, чтобы получить отдельную квоту.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-337">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="bb8c6-338">Ко всем полученным запросам без этого параметра применяется одна квота.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-338">All requests received without this parameter will share the same quota.</span></span>|
||<span data-ttu-id="bb8c6-339">startTime endTime</span><span class="sxs-lookup"><span data-stu-id="bb8c6-339">startTime endTime</span></span>|<span data-ttu-id="bb8c6-340">Необязательные значения даты и времени (в формате UTC), указывающие диапазон времени появления возвращаемого контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-340">Optional datetimes (UTC) that indicate the time range of content to return, based on when the content became available.</span></span> <span data-ttu-id="bb8c6-341">Диапазон времени включает значение _startTime_ (_startTime_ <= contentCreated), но не включает значение _endTime_ (_contentCreated_ < endTime), что позволяет просматривать доступный контент по непересекающимся последовательным интервалам времени.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-341">The time range is inclusive with respect to  _startTime_ ( _startTime_ <= contentCreated) and exclusive with respect to _endTime_ (_contentCreated_ < endTime), so that non-overlapping, incrementing time intervals can used to page through available content.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-342">ГГГГ-ММ-ДД</span><span class="sxs-lookup"><span data-stu-id="bb8c6-342">YYYY-MM-DD</span></span></p></li><li><p><span data-ttu-id="bb8c6-343">ГГГГ-ММ-ДДТЧЧ:ММ</span><span class="sxs-lookup"><span data-stu-id="bb8c6-343">YYYY-MM-DDTHH:MM</span></span></p></li><li><p><span data-ttu-id="bb8c6-344">ГГГГ-ММ-ДДТЧЧ:ММ:СС</span><span class="sxs-lookup"><span data-stu-id="bb8c6-344">YYYY-MM-DDTHH:MM:SS</span></span></p></li></ul><span data-ttu-id="bb8c6-345">Необходимо указать оба значения (или пропустить оба значения), а интервал между ними не должен превышать 24 часа. При этом со времени начала должно пройти не более 7 дней.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-345">Both must be specified (or both omitted) and they must be no more than 24 hours apart, with the start time no more than 7 days in the past.</span></span> <span data-ttu-id="bb8c6-346">По умолчанию, если пропустить значения _startTime_ и _endTime_, возвращается контент, появившийся за последние 24 часа.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-346">By default, if  _startTime_ and _endTime_ are omitted, the content available in the last 24 hours is returned.</span></span>|
|<span data-ttu-id="bb8c6-347">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-347">**Response**</span></span>|<span data-ttu-id="bb8c6-348">Массив JSON</span><span class="sxs-lookup"><span data-stu-id="bb8c6-348">JSON array</span></span>|<span data-ttu-id="bb8c6-349">Уведомления будут представлены объектами JSON со следующими свойствами:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-349">The notifications will be represented by JSON objects with the following properties:</span></span> <ul><li><span data-ttu-id="bb8c6-350">**contentType.** Указывает тип контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-350">**contentType**: indicates the content type.</span></span></li><li><span data-ttu-id="bb8c6-351">**contentId.** Непрозрачная строка, однозначно определяющая контент.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-351">**contentId**: an opaque string that uniquely identifies the content.</span></span></li><li><span data-ttu-id="bb8c6-352">**contentUri.** URL-адрес, используемый при получении контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-352">**contentUri**: the URL to use when retrieving the content.</span></span> </li><li><span data-ttu-id="bb8c6-353">**contentCreated.** Дата и время появления контента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-353">**contentCreated**: the datetime when the content was made available.</span></span></li><li><span data-ttu-id="bb8c6-354">**contentExpiration.** Дата и время, после которых контент больше не будет доступен для получения.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-354">**contentExpiration**: the datetime after which the content will no longer be available for retrieval.</span></span></li><li><span data-ttu-id="bb8c6-355">**notificationSent.** Дата и время отправки уведомления.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-355">**notificationSent**: the datetime when the notification was sent.</span></span></li><li><span data-ttu-id="bb8c6-356">**notificationStatus.** Указывает, была ли попытка отправки уведомления успешной.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-356">**notificationStatus**: indicates the success or failure of the notification attempt.</span></span></li></ul>|

#### <a name="sample-request"></a><span data-ttu-id="bb8c6-357">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-357">Sample request</span></span>

```json
GET {root}/subscriptions/notifications?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="bb8c6-358">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-358">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "contentType": "Audit.SharePoint",
        "contentId": "492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentUri": "https://manage.office.com/api/v1.0/f28ab78a-d401-4060-8012-736e373933eb/activity/feed/audit/492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentCreated": "2015-05-23T17:35:00.000Z",
        "contentExpiration": "2015-05-30T17:35:00.000Z",
        "notificationSent": "2015-05-23T17:36:00.000Z",
        "notificationStatus": "success"

    },
    ...
]

```


### <a name="pagination"></a><span data-ttu-id="bb8c6-359">Разбивка на страницы</span><span class="sxs-lookup"><span data-stu-id="bb8c6-359">Pagination</span></span>

<span data-ttu-id="bb8c6-360">При выводе журнала уведомлений за определенный диапазон времени количество возвращаемых результатов ограничивается во избежание появления просроченных откликов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-360">When listing notification history for a time range, the number of results returned is limited to prevent response timeouts.</span></span> <span data-ttu-id="bb8c6-361">Если за указанный диапазон времени возвращается больше результатов, чем помещается в один отклик, то результаты усекаются, а к отклику добавляется заголовок с URL-адресом для получения следующей страницы результатов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-361">If there are more results in the specified time range than can be returned in a single response, the results are truncated and a header is added to the response indicating the URL to use to retrieve the next page of results.</span></span> <span data-ttu-id="bb8c6-362">URL-адрес будет содержать те же параметры _startTime_ и _endTime_, которые были указаны в исходном запросе, вместе с параметрами, указывающими внутренний ИД следующей страницы.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-362">The URL will contain the same  _startTime_ and _endTime_ parameters that were specified in the original request, together with a parameter indicating the internal ID of the next page.</span></span> <span data-ttu-id="bb8c6-363">Если значения _startTime_ и _endTime_ не были указаны в исходном запросе, то будут заданы даты для 24-часового интервала, предшествующего первоначальному запросу.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-363">If _startTime_ and _endTime_ were not specified in the original request, they will be set to reflect the 24-hour interval that preceded the original request.</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
NextPageUrl: https://manage.office.com/api/v1/{tenant_id}/activity/feed/subscriptions/content?contentType=Audit.SharePoint&amp;startTime=2015-10-01&amp;endTime=2015-10-02&amp;nextPage=2015101900R022885001761

```

<span data-ttu-id="bb8c6-364">Чтобы получить список доступного контента за указанный диапазон времени, вы можете извлекать страницы, пока не будет получен отклик без заголовка **NextPageUrl**.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-364">To list all available content for a specified time range, you might need to retrieve multiple pages until a response without the **NextPageUrl** header is received.</span></span>

## <a name="retrieve-resource-friendly-names"></a><span data-ttu-id="bb8c6-365">Получение понятных имен ресурсов</span><span class="sxs-lookup"><span data-stu-id="bb8c6-365">Retrieve resource friendly names</span></span>

<span data-ttu-id="bb8c6-366">Эта операция получает понятные имена указанных по GUID объектов из веб-канала данных.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-366">This operation retrieves friendly names for objects in the data feed identified by guids.</span></span> <span data-ttu-id="bb8c6-367">В настоящее время поддерживается только объект DlpSensitiveType.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-367">Currently "DlpSensitiveType" is the only supported object.</span></span> 


||<span data-ttu-id="bb8c6-368">Подписка</span><span class="sxs-lookup"><span data-stu-id="bb8c6-368">Subscription</span></span>|<span data-ttu-id="bb8c6-369">Описание</span><span class="sxs-lookup"><span data-stu-id="bb8c6-369">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb8c6-370">**Путь**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-370">**Path**</span></span>| `/resources/dlpSensitiveTypes`||
|<span data-ttu-id="bb8c6-371">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-371">**Parameters**</span></span>|<span data-ttu-id="bb8c6-372">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="bb8c6-372">PublisherIdentifier</span></span>|<span data-ttu-id="bb8c6-373">GUID клиента поставщика, который обращается к API из кода.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-373">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="bb8c6-374">Это **не** GUID приложения или пользователя, работающего с приложением, а GUID компании, написавшей код.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-374">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="bb8c6-375">Этот параметр используется для регулирования частоты запросов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-375">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="bb8c6-376">Убедитесь, что этот параметр указан во всех отправляемых запросах, чтобы получить отдельную квоту.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-376">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="bb8c6-377">Ко всем полученным запросам без этого параметра применяется одна квота.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-377">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="bb8c6-378">**Заголовка**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-378">**Headers**</span></span>|<span data-ttu-id="bb8c6-379">Accept-Language</span><span class="sxs-lookup"><span data-stu-id="bb8c6-379">Accept-Language</span></span>|<span data-ttu-id="bb8c6-380">Заголовок, указывающий нужный язык для локализованных имен.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-380">Header to specify the desired language for localized names.</span></span> <span data-ttu-id="bb8c6-381">Например, используйте значение "en-US" для английского и "es" для испанского.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-381">For example, use "en-US" for English or "es" for Spanish.</span></span> <span data-ttu-id="bb8c6-382">Если этот заголовок отсутствует, возвращается язык по умолчанию (en-US).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-382">The default language (en-US) will be returned if this header is not present.</span></span>|
|<span data-ttu-id="bb8c6-383">**Основной текст**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-383">**Body**</span></span>|<span data-ttu-id="bb8c6-384">(пусто)</span><span class="sxs-lookup"><span data-stu-id="bb8c6-384">(empty)</span></span>||
|<span data-ttu-id="bb8c6-385">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="bb8c6-385">**Response**</span></span>|<span data-ttu-id="bb8c6-386">Массив JSON</span><span class="sxs-lookup"><span data-stu-id="bb8c6-386">JSON array</span></span>|<span data-ttu-id="bb8c6-387">Доступный контент будет представлен объектами JSON со следующими свойствами:</span><span class="sxs-lookup"><span data-stu-id="bb8c6-387">The available content will be represented by JSON objects with the following properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-388"><b>id.</b> Указывает GUID типа конфиденциальной информации.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-388"><b>id</b>: Indicates the guid of the sensitive information type.</span></span></p></li><li><p><span data-ttu-id="bb8c6-389"><b>name.</b> Понятное имя типа конфиденциальной информации.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-389"><b>name</b>: The friendly name of the sensitive information type.</span></span></p></li></ul>|

#### <a name="sample-request"></a><span data-ttu-id="bb8c6-390">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-390">Sample request</span></span>

```json
GET {root}/resources/dlpSensitiveTypes?PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg
Accept-Language: {language code} 

```

#### <a name="sample-response"></a><span data-ttu-id="bb8c6-391">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="bb8c6-391">Sample response</span></span>

```json
HTTP/1.1 200 OK

[
    {
        "id": "50842eb7-edc8-4019-85dd-5a5c1f2bb085",
        "name": "CreditCardNumber"
    }, 
    {
        "id": "0e9b3178-9678-47dd-a509-37222ca96b42",
        "name": "EUDebitCardNumber"
    }, 
    ...
    {
    }
]

```

## <a name="api-throttling"></a><span data-ttu-id="bb8c6-392">Регулирование API</span><span class="sxs-lookup"><span data-stu-id="bb8c6-392">API throttling</span></span>

<span data-ttu-id="bb8c6-393">В организациях, обращающихся к журналам аудита с помощью API действий управления Office 365, применялись ограничения регулирования на уровне издателя.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-393">Organizations that access auditing logs through the Office 365 Management Activity API were restricted by throttling limits at the publisher level.</span></span> <span data-ttu-id="bb8c6-394">Это означает, что для извлечения данных издателем от имени нескольких клиентов ограничение распространялось на всех этих клиентов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-394">This means that for a publisher pulling data on behalf of multiple customers, the limit was shared by all those customers.</span></span>

<span data-ttu-id="bb8c6-395">Мы переходим с ограничения на уровне издателя к ограничению на уровне клиента.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-395">We're moving from a publisher-level limit to a tenant-level limit.</span></span> <span data-ttu-id="bb8c6-396">В результате каждая организация будет иметь собственную полностью выделенную квоту пропускной способности для доступа к данным аудита.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-396">The result is that each organization will get their own fully allocated bandwidth quota to access their auditing data.</span></span> <span data-ttu-id="bb8c6-397">Для всех организаций изначально выделяется базовый уровень 2 000 запросов в минуту.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-397">All organizations are initially allocated a baseline of 2,000 requests per minute.</span></span> <span data-ttu-id="bb8c6-398">Это не статический, предварительно определенный предел, а моделирующийся на основе сочетания факторов, включая число рабочих мест в организации и получение организациями Office 365 и Microsoft 365 E5 вдвое большей пропускной способности по сравнению с организациями без плана E5.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-398">This is not a static, predefined limit but is modeled on a combination of factors including the number of seats in the organization and that Office 365 and Microsoft 365 E5 organizations will get approximately twice as much bandwidth as non-E5 organizations.</span></span> <span data-ttu-id="bb8c6-399">Для защиты работоспособности службы также будет использоваться ограничение максимальной пропускной способности.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-399">There will also be cap on the maximum bandwidth to protect the health of the service.</span></span>

<span data-ttu-id="bb8c6-400">Дополнительные сведения см. в разделе "Доступ с высокой пропускной способностью к API действий управления Office 365" статьи [Расширенный аудит в Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/advanced-audit#high-bandwidth-access-to-the-office-365-management-activity-api).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-400">For more information, see the "High-bandwidth access to the Office 365 Management Activity API" section in [Advanced audit in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/advanced-audit#high-bandwidth-access-to-the-office-365-management-activity-api).</span></span>

> [!NOTE] 
> <span data-ttu-id="bb8c6-401">Хотя каждый клиент может изначально отправлять до 2 000 запросов в минуту, корпорация Майкрософт не может гарантировать скорость отклика.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-401">Even though each tenant can initially submit up to 2,000 requests per minute, Microsoft cannot guarantee a response rate.</span></span> <span data-ttu-id="bb8c6-402">Она зависит от различных факторов, таких как производительность клиентской системы, а также мощность и скорость сети.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-402">The response rate depends on various factors, such as client system performance, network capacity, and network speed.</span></span> 

## <a name="errors"></a><span data-ttu-id="bb8c6-403">Ошибки</span><span class="sxs-lookup"><span data-stu-id="bb8c6-403">Errors</span></span>

<span data-ttu-id="bb8c6-404">Когда служба обнаруживает ошибку, она возвращает отправителю вызова соответствующий код отклика, используя стандартный синтаксис кодов ошибок HTTP.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-404">When the service encounters an error, it will report the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="bb8c6-405">.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-405">.</span></span> <span data-ttu-id="bb8c6-406">Дополнительные сведения включены в текст неудачного запроса в виде одного объекта JSON.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-406">Additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="bb8c6-407">Ниже приведен пример полного текста ошибки JSON.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-407">An example of a full JSON error body is shown below:</span></span> 

```json

{ 
    "error":{ 
        "code":"AF50000",
        "message": "An internal server error occurred. Retry the request."
    } 
}

```


|||
|:-----|:-----|
|<span data-ttu-id="bb8c6-408">Код</span><span class="sxs-lookup"><span data-stu-id="bb8c6-408">Code</span></span>|<span data-ttu-id="bb8c6-409">Сообщение</span><span class="sxs-lookup"><span data-stu-id="bb8c6-409">Message</span></span>|
|<span data-ttu-id="bb8c6-410">AF10001</span><span class="sxs-lookup"><span data-stu-id="bb8c6-410">AF10001</span></span>|<span data-ttu-id="bb8c6-411">Набор разрешений ({0}), отправленный в запросе, не включал ожидаемое разрешение **ActivityFeed.Read**.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-411">The permission set ({0}) sent in the request did not include the expected permission **ActivityFeed.Read**.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-412">{0} — набор разрешений в маркере доступа.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-412">{0} = the permission set in the access token.</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-413">AF20001</span><span class="sxs-lookup"><span data-stu-id="bb8c6-413">AF20001</span></span>|<span data-ttu-id="bb8c6-414">Отсутствующий параметр: {0}.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-414">Missing parameter: {0}.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-415">{0} — имя отсутствующего параметра.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-415">{0} = the name of the missing parameter.</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-416">AF20002</span><span class="sxs-lookup"><span data-stu-id="bb8c6-416">AF20002</span></span>|<span data-ttu-id="bb8c6-417">Недопустимый тип параметра: {0}.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-417">Invalid parameter type: {0}.</span></span> <span data-ttu-id="bb8c6-418">Ожидаемый тип: {1}</span><span class="sxs-lookup"><span data-stu-id="bb8c6-418">Expected type: {1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-419">{0} — имя недопустимого параметра.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-419">{0} = the name of the invalid parameter.</span></span></p></li><li><p><span data-ttu-id="bb8c6-420">{1} — ожидаемый тип (int, datetime, guid).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-420">{1} = the expected type (int, datetime, guid).</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-421">AF20003</span><span class="sxs-lookup"><span data-stu-id="bb8c6-421">AF20003</span></span>|<span data-ttu-id="bb8c6-422">Время окончания срока действия ({0}) уже прошло.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-422">Expiration {0} provided is set to past date and time.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-423">{0} — время окончания срока действия, переданное в вызове API.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-423">{0} = the expiration passed in the API call.</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-424">AF20010</span><span class="sxs-lookup"><span data-stu-id="bb8c6-424">AF20010</span></span>|<span data-ttu-id="bb8c6-425">ИД клиента, переданный в URL-адресе ({0}), не совпадает с ИД клиента в маркере доступа ({1}).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-425">The tenant ID passed in the URL ({0}) does not match the tenant ID passed in the access token ({1}).</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-426">{0} — ИД клиента, переданный в URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-426">{0} = tenant ID passed in the URL</span></span></p></li><li><p><span data-ttu-id="bb8c6-427">{1} — ИД клиента, переданный в маркере доступа.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-427">{1} = tenant ID passed in the access token</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-428">AF20011</span><span class="sxs-lookup"><span data-stu-id="bb8c6-428">AF20011</span></span>|<span data-ttu-id="bb8c6-429">Указанный ИД клиента ({0}) не существует в системе или был удален.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-429">Specified tenant ID ({0}) does not exist in the system or has been deleted.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>   <span data-ttu-id="bb8c6-430">{0} — ИД клиента, переданный в URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-430">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-431">AF20012</span><span class="sxs-lookup"><span data-stu-id="bb8c6-431">AF20012</span></span>|<span data-ttu-id="bb8c6-432">Указанный ИД клиента ({0}) неправильно настроен в системе.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-432">Specified tenant ID ({0}) is incorrectly configured in the system.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>    <span data-ttu-id="bb8c6-433">{0} — ИД клиента, переданный в URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-433">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-434">AF20013</span><span class="sxs-lookup"><span data-stu-id="bb8c6-434">AF20013</span></span>|<span data-ttu-id="bb8c6-435">ИД клиента, переданный в URL-адресе ({0}), не является допустимым GUID.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-435">The tenant ID passed in the URL ({0}) is not a valid GUID.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p> <span data-ttu-id="bb8c6-436">{0} — ИД клиента, переданный в URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-436">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-437">AF20020</span><span class="sxs-lookup"><span data-stu-id="bb8c6-437">AF20020</span></span>|<span data-ttu-id="bb8c6-438">Указанный тип контента не является допустимым.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-438">The specified content type is not valid.</span></span>|
|<span data-ttu-id="bb8c6-439">AF20021</span><span class="sxs-lookup"><span data-stu-id="bb8c6-439">AF20021</span></span>|<span data-ttu-id="bb8c6-440">Не удалось проверить конечную точку веб-перехватчика {{0}).</span><span class="sxs-lookup"><span data-stu-id="bb8c6-440">The webhook endpoint {{0}) could not be validated.</span></span> <span data-ttu-id="bb8c6-441">{1}</span><span class="sxs-lookup"><span data-stu-id="bb8c6-441">{1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-442">{0} — адрес веб-перехватчика.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-442">{0} = webhook address.</span></span></p></li><li><p><span data-ttu-id="bb8c6-443">{1} — "Конечная точка не вернула код HTTP 200"</span><span class="sxs-lookup"><span data-stu-id="bb8c6-443">{1} = "The endpoint did not return HTTP 200."</span></span> <span data-ttu-id="bb8c6-444">или "Адрес должен начинаться с HTTPS".</span><span class="sxs-lookup"><span data-stu-id="bb8c6-444">or "The address must begin with HTTPS."</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-445">AF20022</span><span class="sxs-lookup"><span data-stu-id="bb8c6-445">AF20022</span></span>|<span data-ttu-id="bb8c6-446">Подписка для указанного типа контента не найдена.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-446">No subscription found for the specified content type.</span></span>|
|<span data-ttu-id="bb8c6-447">AF20023</span><span class="sxs-lookup"><span data-stu-id="bb8c6-447">AF20023</span></span>|<span data-ttu-id="bb8c6-448">Подписку отключил {0}.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-448">The subscription was disabled by {0}.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-449">{0} — "администратор клиента" или "администратор службы"</span><span class="sxs-lookup"><span data-stu-id="bb8c6-449">{0} = "a tenant admin" or "a service admin"</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-450">AF20030</span><span class="sxs-lookup"><span data-stu-id="bb8c6-450">AF20030</span></span>|<span data-ttu-id="bb8c6-451">Необходимо указать время начала и окончания (или пропустить оба значения), а интервал между ними не должен превышать 24 часа. При этом со времени начала должно пройти не более 7 дней.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-451">Start time and end time must both be specified (or both omitted) and must be less than or equal to 24 hours apart, with the start time no more than 7 days in the past.</span></span>|
|<span data-ttu-id="bb8c6-452">AF20031</span><span class="sxs-lookup"><span data-stu-id="bb8c6-452">AF20031</span></span>|<span data-ttu-id="bb8c6-453">Недопустимые входные данные nextPage: {0}.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-453">Invalid nextPage Input: {0}.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-454">{0} — индикатор следующей страницы, переданный в URL-адресе</span><span class="sxs-lookup"><span data-stu-id="bb8c6-454">{0} = the next page indicator passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-455">AF20050</span><span class="sxs-lookup"><span data-stu-id="bb8c6-455">AF20050</span></span>|<span data-ttu-id="bb8c6-456">Указанный контент ({0}) не существует.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-456">The specified content ({0}) does not exist.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-457">{0} — идентификатор или URL-адрес ресурса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-457">{0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-458">AF20051</span><span class="sxs-lookup"><span data-stu-id="bb8c6-458">AF20051</span></span>|<span data-ttu-id="bb8c6-459">Контент, запрашиваемый с помощью ключа {0}, уже устарел.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-459">Content requested with the key {0} has already expired.</span></span> <span data-ttu-id="bb8c6-460">Контент старше 7 дней невозможно получить.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-460">Content older than 7 days cannot be retrieved.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-461">• {0} — идентификатор или URL-адрес ресурса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-461">•    {0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-462">AF20052</span><span class="sxs-lookup"><span data-stu-id="bb8c6-462">AF20052</span></span>|<span data-ttu-id="bb8c6-463">Недопустимый ИД контента {0} в URL-адресе</span><span class="sxs-lookup"><span data-stu-id="bb8c6-463">Content ID {0} in the URL is invalid.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-464">{0} — идентификатор или URL-адрес ресурса</span><span class="sxs-lookup"><span data-stu-id="bb8c6-464">{0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-465">AF20053</span><span class="sxs-lookup"><span data-stu-id="bb8c6-465">AF20053</span></span>|<span data-ttu-id="bb8c6-466">В заголовке Accept-Language можно указать только один язык.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-466">Only one language may be present in the Accept-Language header.</span></span>|
|<span data-ttu-id="bb8c6-467">AF20054</span><span class="sxs-lookup"><span data-stu-id="bb8c6-467">AF20054</span></span>|<span data-ttu-id="bb8c6-468">Недопустимый синтаксис в заголовке Accept-Language.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-468">Invalid syntax in Accept-Language header.</span></span>|
|<span data-ttu-id="bb8c6-469">AF429</span><span class="sxs-lookup"><span data-stu-id="bb8c6-469">AF429</span></span>|<span data-ttu-id="bb8c6-470">Слишком много запросов.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-470">Too many requests.</span></span> <span data-ttu-id="bb8c6-471">Method={0}, PublisherId={1}</span><span class="sxs-lookup"><span data-stu-id="bb8c6-471">Method={0}, PublisherId={1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="bb8c6-472">{0} — метод HTTP</span><span class="sxs-lookup"><span data-stu-id="bb8c6-472">{0} = HTTP Method</span></span></p></li><li><p><span data-ttu-id="bb8c6-473">{1} — GUID клиента, используемый в качестве параметра PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="bb8c6-473">{1} = Tenant GUID used as PublisherIdentifier</span></span></p></li></ul>|
|<span data-ttu-id="bb8c6-474">AF50000</span><span class="sxs-lookup"><span data-stu-id="bb8c6-474">AF50000</span></span>|<span data-ttu-id="bb8c6-475">Произошла внутренняя ошибка.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-475">An internal error occurred.</span></span> <span data-ttu-id="bb8c6-476">Повторите запрос.</span><span class="sxs-lookup"><span data-stu-id="bb8c6-476">Retry the request.</span></span>|
