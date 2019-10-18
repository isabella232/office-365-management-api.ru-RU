---
ms.TocTitle: Office 365 Service Communications API reference
title: 'Справочник по API сообщений о службах Office 365 '
description: 'Этот API используется для доступа к следующим данным: список служб, текущее состояние, изменения состояния, сообщения.'
ms.ContentId: d0b9341a-b205-5442-1c20-8fb56407351d
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 427c741f623f46962c3cd6818adbb64bfc0f1e7a
ms.sourcegitcommit: 0e6d71ad2375e5d1fc72d6893724511c08840c27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "37131426"
---
# <a name="office-365-service-communications-api-reference"></a><span data-ttu-id="8e5c0-103">Справочник по API сообщений о службах Office 365 </span><span class="sxs-lookup"><span data-stu-id="8e5c0-103">Office 365 Service Communications API reference (preview)</span></span>

<span data-ttu-id="8e5c0-104">С помощью API сообщений о службах Office 365 версии 2 можно получать доступ к следующим данным:</span><span class="sxs-lookup"><span data-stu-id="8e5c0-104">You can use the Office 365 Service Communications API V2 to access the following data:</span></span>

- <span data-ttu-id="8e5c0-105">**Получение служб.** Получение списка подписанных служб.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-105">**Get Services**: Get the list of subscribed services.</span></span>
    
- <span data-ttu-id="8e5c0-106">**Получение текущего состояния.** Обновляемое в реальном времени представление текущих инцидентов.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-106">**Get Current Status**: Get a real-time view of current and ongoing service incidents and maintenance events</span></span>
    
- <span data-ttu-id="8e5c0-107">**Получение сведений об изменении состояния.** Представление инцидентов в хронологическом порядке.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-107">**Get Historical Status**: Get a historical view of service health, including service incidents and maintenance events.</span></span>
    
- <span data-ttu-id="8e5c0-108">**Получение сообщений.** Поиск сообщений об инцидентах, а также данных Центра сообщений.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-108">**Get Messages**: Find Incident, Planned Maintenance, and Message Center communications.</span></span>
    
<span data-ttu-id="8e5c0-109">В настоящий момент API сообщений о службах Office 365 содержит данные для облачных служб Office 365, Yammer, Dynamics CRM и Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-109">Currently, the Office 365 Service Communications API contains data for Office 365, Yammer, Dynamics CRM and Microsoft Intune cloud services.</span></span>

## <a name="the-fundamentals"></a><span data-ttu-id="8e5c0-110">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="8e5c0-110">The fundamentals</span></span>

<span data-ttu-id="8e5c0-111">URL-адрес API включает идентификатор клиента, ограничивающий область действия операций одним клиентом:</span><span class="sxs-lookup"><span data-stu-id="8e5c0-111">The root URL of the API includes a tenant identifier that scopes the operations to a single tenant:</span></span>

```http
https://manage.office.com/api/v1.0/{tenant_identifier}/ServiceComms/{operation}
```

<span data-ttu-id="8e5c0-112">**API сообщений о службах Office 365** — это служба REST, позволяющая разрабатывать решения на любом языке и в любой среде внешнего размещения, поддерживающей сертификаты HTTPS и X.509.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-112">The **Office 365 Service Communications API** is a REST service that allows you to develop solutions using any web language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="8e5c0-113">Этот API использует службу **Microsoft Azure Active Directory** и протокол **OAuth2** для проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-113">The API relies on **Microsoft Azure Active Directory** and the **OAuth2** protocol for authentication and authorization.</span></span> <span data-ttu-id="8e5c0-114">Чтобы получить доступ к API из приложения, необходимо сначала зарегистрировать его в Azure AD и задать подходящую область разрешений.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-114">To access the API from your application, you'll need to first register it in Azure AD and configure it with permissions at the appropriate scope.</span></span> <span data-ttu-id="8e5c0-115">Благодаря этому приложение сможет запрашивать маркеры доступа OAuth2, необходимые для вызова API.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-115">This will enable your application to request OAuth2 access tokens necessary for calling the API.</span></span> <span data-ttu-id="8e5c0-116">Дополнительные сведения о регистрации и настройке приложения в Azure AD см. в статье [Начало работы с API управления Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-116">You can find more information about registering and configuring an application in Azure AD at [Office 365 Management APIs getting started](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="8e5c0-117">Для всех запросов к API необходим заголовок Authorization HTTP с действительным маркером доступа JWT OAuth2, полученным из Azure AD и содержащим утверждение **ServiceHealth.Read**. А идентификатор клиента должен быть таким же, как в корневом URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-117">All API requests require an Authorization HTTP header that has a valid OAuth2 JWT access token obtained from Azure AD that contains the **ServiceHealth.Read** claim; and the tenant identifier must match the tenant identifier in the root URL.</span></span>

```json
Authorization: Bearer {OAuth2 token}
```

### <a name="request-headers"></a><span data-ttu-id="8e5c0-118">Заголовки запросов</span><span class="sxs-lookup"><span data-stu-id="8e5c0-118">Request headers</span></span>

<span data-ttu-id="8e5c0-119">Ниже показаны поддерживаемые заголовки запросов для всех операций API сообщений о службах Office 365.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-119">These are the supported request headers for all Office 365 Service Communications API operations.</span></span>

|<span data-ttu-id="8e5c0-120">Заголовок</span><span class="sxs-lookup"><span data-stu-id="8e5c0-120">Header</span></span>|<span data-ttu-id="8e5c0-121">Описание</span><span class="sxs-lookup"><span data-stu-id="8e5c0-121">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="8e5c0-122">**Accept (необязательный)**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-122">**Accept (Optional)**</span></span>|<span data-ttu-id="8e5c0-123">Ниже показаны допустимые представления отклика.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-123">The following are acceptable representations for the response:</span></span><br/><span data-ttu-id="8e5c0-124">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-124">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="8e5c0-125">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-125">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="8e5c0-126">**application/json;odata.metadata=none** [используется по умолчанию, если заголовок не указан]</span><span class="sxs-lookup"><span data-stu-id="8e5c0-126">[The default if header not specified] **application/json;odata.metadata=none**</span></span>|
|<span data-ttu-id="8e5c0-127">**Authorization (обязательный)**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-127">**Authorization (Required)**</span></span>|<span data-ttu-id="8e5c0-128">Маркер авторизации (токен носителя JWT Azure AD) для запроса.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-128">Authorization token (Bearer JWT Azure AD Token) for the request.</span></span>|


<br/>

### <a name="response-headers"></a><span data-ttu-id="8e5c0-129">Заголовки откликов</span><span class="sxs-lookup"><span data-stu-id="8e5c0-129">Response headers</span></span>

<span data-ttu-id="8e5c0-130">Ниже показаны заголовки откликов, возвращаемые для всех операций API сообщений о службах Office 365.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-130">These are the response headers returned for all Office 365 Service Communications API operations:</span></span>

|<span data-ttu-id="8e5c0-131">Заголовок</span><span class="sxs-lookup"><span data-stu-id="8e5c0-131">Header</span></span>|<span data-ttu-id="8e5c0-132">Описание</span><span class="sxs-lookup"><span data-stu-id="8e5c0-132">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="8e5c0-133">**Content-Length**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-133">**Content-Length**</span></span>|<span data-ttu-id="8e5c0-134">Длина основного текста отклика.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-134">The length of the response body.</span></span>|
|<span data-ttu-id="8e5c0-135">**Content-Type**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-135">**Content-Type**</span></span>|<span data-ttu-id="8e5c0-136">Представление отклика:</span><span class="sxs-lookup"><span data-stu-id="8e5c0-136">Representation of the response:</span></span><br/><span data-ttu-id="8e5c0-137">**application/json**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-137">**application/json**</span></span><br/><span data-ttu-id="8e5c0-138">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-138">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="8e5c0-139">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-139">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="8e5c0-140">**application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-140">**application/json;odata.metadata=none**</span></span><br/><span data-ttu-id="8e5c0-141">**odata.streaming=true**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-141">**odata.streaming=true**</span></span>|
|<span data-ttu-id="8e5c0-142">**Cache-Control**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-142">**Cache-Control**</span></span>|<span data-ttu-id="8e5c0-143">Используется для указания директив, которым должны подчиняться все механизмы кэширования в цепочке запросов и откликов.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-143">Used to specify directives that all caching mechanisms along the request/response chain must obey.</span></span>|
|<span data-ttu-id="8e5c0-144">**Pragma**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-144">**Pragma**</span></span>|<span data-ttu-id="8e5c0-145">Поведение для конкретных реализаций.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-145">Implementation-specific behaviors.</span></span>|
|<span data-ttu-id="8e5c0-146">**Expires**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-146">**Expires**</span></span>|<span data-ttu-id="8e5c0-147">Указывает, когда клиент должен сделать ресурс устаревшим.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-147">When the client should make the resource expire.</span></span>|
|<span data-ttu-id="8e5c0-148">**X-Activity-Id**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-148">**X-Activity-Id**</span></span>|<span data-ttu-id="8e5c0-149">Созданный сервером идентификатор действия.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-149">The server-generated activity Id.</span></span>|
|<span data-ttu-id="8e5c0-150">**OData-Version**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-150">**OData-Version**</span></span>|<span data-ttu-id="8e5c0-151">Поддерживаемая версия OData (4.0).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-151">The supported OData Version (4.0).</span></span>|
|<span data-ttu-id="8e5c0-152">**Date**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-152">**Date**</span></span>|<span data-ttu-id="8e5c0-153">Дата отправки отклика с сервера (в формате UTC).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-153">The date in UTC when the response was sent from the server.</span></span>|
|<span data-ttu-id="8e5c0-154">**X-Time-Taken**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-154">**X-Time-Taken**</span></span>|<span data-ttu-id="8e5c0-155">Время, затраченное на создание отклика (мс).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-155">The time it took to generate the response (ms).</span></span>|
|<span data-ttu-id="8e5c0-156">**X-Instance-Name**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-156">**X-Instance-Name**</span></span>|<span data-ttu-id="8e5c0-157">Идентификатор экземпляра Azure, используемого для создания отклика (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-157">The identifier of the Azure instance used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="8e5c0-158">**Server**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-158">**Server**</span></span>|<span data-ttu-id="8e5c0-159">Сервер, используемый для создания отклика (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-159">The server used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="8e5c0-160">**X-ASPNET-Version**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-160">**X-ASPNET-Version**</span></span>|<span data-ttu-id="8e5c0-161">Версия ASP.Net, используемая на сервере, который создал отклик (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-161">The version of ASP.Net used by the server that generated the response (for debugging purposes).</span></span>|
|<span data-ttu-id="8e5c0-162">**X-Powered-By**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-162">**X-Powered-By**</span></span>|<span data-ttu-id="8e5c0-163">Технологии, используемые на сервере, который создал отклик (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-163">The technologies used in the server that generated the response (for debugging purposes).</span></span>|
|||

<br/>

<span data-ttu-id="8e5c0-164">Ниже представлены операции API сообщений о службах Office 365.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-164">Following are the Office 365 Service Communications API operations.</span></span>


## <a name="get-services"></a><span data-ttu-id="8e5c0-165">Получение служб</span><span class="sxs-lookup"><span data-stu-id="8e5c0-165">Get Services</span></span>

<span data-ttu-id="8e5c0-166">Возвращает список подписанных служб.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-166">Returns the list of subscribed services.</span></span>

||<span data-ttu-id="8e5c0-167">Служба</span><span class="sxs-lookup"><span data-stu-id="8e5c0-167">Service</span></span>|<span data-ttu-id="8e5c0-168">Описание</span><span class="sxs-lookup"><span data-stu-id="8e5c0-168">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8e5c0-169">**Путь**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-169">**Path**</span></span>| `/Services`||
|<span data-ttu-id="8e5c0-170">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-170">**Query-option**</span></span>|<span data-ttu-id="8e5c0-171">$select</span><span class="sxs-lookup"><span data-stu-id="8e5c0-171">$select</span></span>|<span data-ttu-id="8e5c0-172">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-172">Pick a subset of properties.</span></span>|
|<span data-ttu-id="8e5c0-173">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-173">**Response**</span></span>|<span data-ttu-id="8e5c0-174">Список объектов Service</span><span class="sxs-lookup"><span data-stu-id="8e5c0-174">List of "Service" entities</span></span>|<span data-ttu-id="8e5c0-175">Объект Service содержит свойства Id (String), DisplayName (String) и FeatureNames (список String).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-175">"Service" entity contains "Id" (String), "DisplayName" (String), and "FeatureNames" (list of Strings).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8e5c0-176">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="8e5c0-176">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Services 
Authorization: Bearer {AAD_Bearer_JWT_Token}

```

### <a name="sample-response"></a><span data-ttu-id="8e5c0-177">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="8e5c0-177">Sample response</span></span>

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


## <a name="get-current-status"></a><span data-ttu-id="8e5c0-178">Получение текущего состояния</span><span class="sxs-lookup"><span data-stu-id="8e5c0-178">Get Current Status</span></span>

<span data-ttu-id="8e5c0-179">Возвращает состояние службы за предыдущие 24 часа.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-179">Returns the status of the service over the previous 24 hours.</span></span>

> [!NOTE] 
> <span data-ttu-id="8e5c0-180">Отклик службы будет содержать состояние и все инциденты за предыдущие 24 часа.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-180">The service response will contain the status and any incidents within the previous 24 hours.</span></span> <span data-ttu-id="8e5c0-181">Возвращаемое значение StatusDate или StatusTime точно соответствует моменту времени 24 часа назад.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-181">The StatusDate or StatusTime value returned will be exactly 24 hours in the past.</span></span> <span data-ttu-id="8e5c0-182">Чтобы получить последнее обновление для конкретного инцидента, используйте функцию получения сообщений и прочтите значение LastUpdatedTime из записи отклика, соответствующего идентификатору инцидента.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-182">To get the last update for a particular incident, use the Get Messages functionality and read the LastUpdatedTime value from the response record that matches your incident ID.</span></span> <br/>

<br/>

||<span data-ttu-id="8e5c0-183">Служба</span><span class="sxs-lookup"><span data-stu-id="8e5c0-183">Service</span></span>|<span data-ttu-id="8e5c0-184">Описание</span><span class="sxs-lookup"><span data-stu-id="8e5c0-184">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8e5c0-185">**Путь**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-185">**Path**</span></span>| `/CurrentStatus`||
|<span data-ttu-id="8e5c0-186">**Фильтр**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-186">**Filter**</span></span>|<span data-ttu-id="8e5c0-187">Workload</span><span class="sxs-lookup"><span data-stu-id="8e5c0-187">Workload</span></span>|<span data-ttu-id="8e5c0-188">Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-188">Filter by workload (String, default: all).</span></span>|
|<span data-ttu-id="8e5c0-189">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-189">**Query-option**</span></span>|<span data-ttu-id="8e5c0-190">$select</span><span class="sxs-lookup"><span data-stu-id="8e5c0-190">$select</span></span>|<span data-ttu-id="8e5c0-191">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-191">Pick a subset of properties.</span></span>|
|<span data-ttu-id="8e5c0-192">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-192">**Response**</span></span>|<span data-ttu-id="8e5c0-193">Список объектов WorkloadStatus.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-193">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="8e5c0-194">Объект WorkloadStatus содержит свойства Id (String), Workload (String), StatusTime (DateTimeOffset), WorkloadDisplayName (String), Status (String), IncidentIds (список String) и FeatureGroupStatusCollection (список объектов FeatureStatus).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-194">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="8e5c0-195">Объект FeatureStatus содержит свойства Feature (String), FeatureGroupDisplayName (String) и FeatureStatus (String).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-195">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8e5c0-196">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="8e5c0-196">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/CurrentStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="8e5c0-197">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="8e5c0-197">Sample response</span></span>

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

### <a name="status-definitions"></a><span data-ttu-id="8e5c0-198">Определения состояний</span><span class="sxs-lookup"><span data-stu-id="8e5c0-198">Status definitions</span></span>

<span data-ttu-id="8e5c0-199">Определения состояний включают следующие значения:</span><span class="sxs-lookup"><span data-stu-id="8e5c0-199">The status definitions include the following values:</span></span> 

- <span data-ttu-id="8e5c0-200">Investigating</span><span class="sxs-lookup"><span data-stu-id="8e5c0-200">Investigating</span></span>
- <span data-ttu-id="8e5c0-201">ServiceDegradation</span><span class="sxs-lookup"><span data-stu-id="8e5c0-201">ServiceDegradation</span></span>
- <span data-ttu-id="8e5c0-202">ServiceInterruption</span><span class="sxs-lookup"><span data-stu-id="8e5c0-202">ServiceInterruption</span></span> 
- <span data-ttu-id="8e5c0-203">RestoringService</span><span class="sxs-lookup"><span data-stu-id="8e5c0-203">RestoringService</span></span>
- <span data-ttu-id="8e5c0-204">ExtendedRecovery</span><span class="sxs-lookup"><span data-stu-id="8e5c0-204">ExtendedRecovery</span></span>
- <span data-ttu-id="8e5c0-205">ServiceRestored</span><span class="sxs-lookup"><span data-stu-id="8e5c0-205">ServiceRestored</span></span>
- <span data-ttu-id="8e5c0-206">PostIncidentReportPublished</span><span class="sxs-lookup"><span data-stu-id="8e5c0-206">PostIncidentReportPublished</span></span> 
- <span data-ttu-id="8e5c0-207">VerifyingService</span><span class="sxs-lookup"><span data-stu-id="8e5c0-207">VerifyingService</span></span>
- <span data-ttu-id="8e5c0-208">ServiceOperational</span><span class="sxs-lookup"><span data-stu-id="8e5c0-208">ServiceOperational</span></span>

<span data-ttu-id="8e5c0-209">Актуальный список и описание этих определений состояния см. в статье [Проверка работоспособности служб Office 365](https://docs.microsoft.com/office365/enterprise/view-service-health#status-definitions).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-209">For an up-to-date list and description of these status definitions, see [How to check Office 365 service health](https://docs.microsoft.com/office365/enterprise/view-service-health#status-definitions).</span></span>


## <a name="get-historical-status"></a><span data-ttu-id="8e5c0-210">Получение сведений об изменении состояния</span><span class="sxs-lookup"><span data-stu-id="8e5c0-210">Get Historical Status</span></span>

<span data-ttu-id="8e5c0-211">Возвращает сведения об изменении состояния службы по дням за определенный диапазон времени.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-211">Returns the historical status of the service, by day, over a certain time range.</span></span>

||<span data-ttu-id="8e5c0-212">Служба</span><span class="sxs-lookup"><span data-stu-id="8e5c0-212">Service</span></span>|<span data-ttu-id="8e5c0-213">Описание</span><span class="sxs-lookup"><span data-stu-id="8e5c0-213">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8e5c0-214">**Путь**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-214">**Path**</span></span>| `/HistoricalStatus`||
|<span data-ttu-id="8e5c0-215">**Фильтры**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-215">**Filters**</span></span>|<span data-ttu-id="8e5c0-216">Workload</span><span class="sxs-lookup"><span data-stu-id="8e5c0-216">Workload</span></span>|<span data-ttu-id="8e5c0-217">Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-217">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="8e5c0-218">StatusTime</span><span class="sxs-lookup"><span data-stu-id="8e5c0-218">StatusTime</span></span>|<span data-ttu-id="8e5c0-219">Фильтрация по дням после StatusTime (DateTimeOffset, значение по умолчанию: 7 дней для ge CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-219">Filter by days greater than StatusTime (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
|<span data-ttu-id="8e5c0-220">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-220">**Query-option**</span></span>|<span data-ttu-id="8e5c0-221">$select</span><span class="sxs-lookup"><span data-stu-id="8e5c0-221">$select</span></span>|<span data-ttu-id="8e5c0-222">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-222">Pick a subset of properties.</span></span>|
|<span data-ttu-id="8e5c0-223">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-223">**Response**</span></span>|<span data-ttu-id="8e5c0-224">Список объектов WorkloadStatus.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-224">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="8e5c0-225">Объект WorkloadStatus содержит свойства Id (String), Workload (String), StatusTime (DateTimeOffset), WorkloadDisplayName (String), Status (String), IncidentIds (список String) и FeatureGroupStatusCollection (список объектов FeatureStatus).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-225">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="8e5c0-226">Объект FeatureStatus содержит свойства Feature (String), FeatureGroupDisplayName (String) и FeatureStatus (String).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-226">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8e5c0-227">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="8e5c0-227">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/HistoricalStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="8e5c0-228">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="8e5c0-228">Sample response</span></span>

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

## <a name="get-messages"></a><span data-ttu-id="8e5c0-229">Получение сообщений</span><span class="sxs-lookup"><span data-stu-id="8e5c0-229">Get Messages</span></span>

<span data-ttu-id="8e5c0-230">Возвращает сообщения о службе за определенный диапазон времени.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-230">Returns the messages about the service over a certain time range.</span></span> <span data-ttu-id="8e5c0-231">Используйте фильтр по типу, чтобы просмотреть сообщения об инцидентах обслуживания, плановом обслуживании или из Центра сообщений.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-231">Use the type filter to filter for "Service Incident", "Planned Maintenance", or "Message Center" messages.</span></span>

||<span data-ttu-id="8e5c0-232">Служба</span><span class="sxs-lookup"><span data-stu-id="8e5c0-232">Service</span></span>|<span data-ttu-id="8e5c0-233">Описание</span><span class="sxs-lookup"><span data-stu-id="8e5c0-233">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8e5c0-234">**Путь**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-234">**Path**</span></span>| `/Messages`||
|<span data-ttu-id="8e5c0-235">**Фильтры**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-235">**Filters**</span></span>|<span data-ttu-id="8e5c0-236">Workload</span><span class="sxs-lookup"><span data-stu-id="8e5c0-236">Workload</span></span>|<span data-ttu-id="8e5c0-237">Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-237">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="8e5c0-238">StartTime</span><span class="sxs-lookup"><span data-stu-id="8e5c0-238">StartTime</span></span>|<span data-ttu-id="8e5c0-239">Фильтрация по времени начала (DateTimeOffset, значение по умолчанию: 7 дней для ge CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-239">Filter by Start Time (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
||<span data-ttu-id="8e5c0-240">EndTime</span><span class="sxs-lookup"><span data-stu-id="8e5c0-240">EndTime</span></span>|<span data-ttu-id="8e5c0-241">Фильтрация по времени окончания (DateTimeOffset, значение по умолчанию: le CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-241">Filter by End Time (DateTimeOffset, default: le CurrentTime).</span></span>|
||<span data-ttu-id="8e5c0-242">MessageType</span><span class="sxs-lookup"><span data-stu-id="8e5c0-242">MessageType</span></span>|<span data-ttu-id="8e5c0-243">Фильтрация по MessageType (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-243">Filter by MessageType (String, default: all).</span></span>|
||<span data-ttu-id="8e5c0-244">ID</span><span class="sxs-lookup"><span data-stu-id="8e5c0-244">ID</span></span>|<span data-ttu-id="8e5c0-245">Фильтрация по идентификатору (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-245">Filter by ID (String, default: all).</span></span>|
|<span data-ttu-id="8e5c0-246">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-246">**Query-option**</span></span>|<span data-ttu-id="8e5c0-247">$select</span><span class="sxs-lookup"><span data-stu-id="8e5c0-247">$select</span></span>|<span data-ttu-id="8e5c0-248">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-248">Pick a subset of properties.</span></span>|
||<span data-ttu-id="8e5c0-249">$top</span><span class="sxs-lookup"><span data-stu-id="8e5c0-249">$top</span></span>|<span data-ttu-id="8e5c0-250">Выбор максимального количества результатов (используемое по умолчанию и максимальное значение: $top=100).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-250">Pick the top number of results (default and max $top=100).</span></span>|
||<span data-ttu-id="8e5c0-251">$skip</span><span class="sxs-lookup"><span data-stu-id="8e5c0-251">$skip</span></span>|<span data-ttu-id="8e5c0-252">Пропуск определенного количества результатов (значение по умолчанию: $skip=0).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-252">Skip number of results (default: $skip=0).</span></span>|
|<span data-ttu-id="8e5c0-253">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="8e5c0-253">**Response**</span></span>|<span data-ttu-id="8e5c0-254">Список объектов Message.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-254">List of "Message" entities.</span></span>|<span data-ttu-id="8e5c0-255">Объект Message содержит свойства Id (String), StartTime (DateTimeOffset), EndTime (DateTimeOffset), Status (String), Messages (список объектов MessageHistory), LastUpdatedTime (DateTimeOffset), Workload (String), WorkloadDisplayName (String), Feature (String), FeatureDisplayName (String), MessageType (Enum, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-255">"Message" entity contains "Id" (String), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (String), "Messages" (list of "MessageHistory" entity), "LastUpdatedTime" (DateTimeOffset), "Workload" (String), "WorkloadDisplayName" (String), "Feature" (String), "FeatureDisplayName" (String), "MessageType" (Enum, default: all).</span></span><br/><br/><span data-ttu-id="8e5c0-256">Объект MessageHistory содержит свойства PublishedTime (DateTimeOffset), MessageText (String).</span><span class="sxs-lookup"><span data-stu-id="8e5c0-256">"MessageHistory" entity contains "PublishedTime" (DateTimeOffset), "MessageText" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8e5c0-257">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="8e5c0-257">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Messages
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="8e5c0-258">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="8e5c0-258">Sample response</span></span>

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


## <a name="errors"></a><span data-ttu-id="8e5c0-259">Ошибки</span><span class="sxs-lookup"><span data-stu-id="8e5c0-259">Errors</span></span>

<span data-ttu-id="8e5c0-260">Когда служба обнаруживает ошибку, она возвращает отправителю вызова соответствующий код отклика, используя стандартный синтаксис кодов ошибок HTTP.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-260">When the service encounters an error, it reports the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="8e5c0-261">Согласно [спецификации OData версии 4](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html) дополнительные сведения включены в текст запроса, вернувшего код ошибки, в виде одного объекта JSON.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-261">As per [OData V4 specification](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="8e5c0-262">Ниже представлен пример полного текста ошибки JSON.</span><span class="sxs-lookup"><span data-stu-id="8e5c0-262">The following is an example of a full JSON error body:</span></span>


```json
{ 
    "error":{ 
        "code":"AF5000.  An internal server error occurred.",
        "message": "Retry the request." 
    } 
}
```

