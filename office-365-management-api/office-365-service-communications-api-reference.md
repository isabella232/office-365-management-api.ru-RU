---
ms.TocTitle: Office 365 Service Communications API reference (preview)
title: Справочник по API сообщений о службах Office 365 (предварительная версия)
description: 'Этот API используется для доступа к следующим данным: список служб, текущее состояние, изменения состояния, сообщения.'
ms.ContentId: d0b9341a-b205-5442-1c20-8fb56407351d
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 9b38c4ee73f18bf10c7fa7cbb5b323740dfb5a7e
ms.sourcegitcommit: 5b1eaeb7f262b7b9f7ab30ccb9f10878814153ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "32223975"
---
# <a name="office-365-service-communications-api-reference-preview"></a><span data-ttu-id="96db9-103">Справочник по API сообщений о службах Office 365 (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="96db9-103">Office 365 Service Communications API reference (preview)</span></span>

> [!NOTE] 
> <span data-ttu-id="96db9-104">В этой документации рассмотрены функции, доступные в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="96db9-104">This documentation covers features that are currently in preview.</span></span>

<span data-ttu-id="96db9-105">С помощью API сообщений о службах Office 365 версии 2 можно получать доступ к следующим данным:</span><span class="sxs-lookup"><span data-stu-id="96db9-105">You can use the Office 365 Service Communications API V2 to access the following data:</span></span>

- <span data-ttu-id="96db9-106">**Получение служб.** Получение списка подписанных служб.</span><span class="sxs-lookup"><span data-stu-id="96db9-106">**Get Services**: Get the list of subscribed services.</span></span>
    
- <span data-ttu-id="96db9-107">**Получение текущего состояния.** Обновляемое в реальном времени представление текущих инцидентов и событий обслуживания.</span><span class="sxs-lookup"><span data-stu-id="96db9-107">**Get Current Status**: Get a real-time view of current and ongoing service incidents and maintenance events</span></span>
    
- <span data-ttu-id="96db9-108">**Получение сведений об изменении состояния.** Представление журнала работоспособности служб, включающего инциденты и события обслуживания.</span><span class="sxs-lookup"><span data-stu-id="96db9-108">**Get Historical Status**: Get a historical view of service health, including service incidents and maintenance events.</span></span>
    
- <span data-ttu-id="96db9-109">**Получение сообщений.** Поиск сообщений об инцидентах и плановом обслуживании, а также данных Центра сообщений.</span><span class="sxs-lookup"><span data-stu-id="96db9-109">**Get Messages**: Find Incident, Planned Maintenance, and Message Center communications.</span></span>
    
<span data-ttu-id="96db9-110">В настоящее время API сообщений о службах Office 365 содержит данные о следующих службах: Dynamics CRM, Dynamics Marketing, Exchange Online, Exchange Online Protection, служба идентификации, служба управления мобильными устройствами, Центр администратора партнера Office 365, OneDrive для бизнеса, Parature, OneDrive для бизнеса, Power BI для Office 365, служба управления правами, SharePoint Online, служба администратора SHD, Skype для бизнеса, Social Engagement и Yammer корпоративный.</span><span class="sxs-lookup"><span data-stu-id="96db9-110">Currently, the Office 365 Service Communications API contains data for the following services: Dynamics CRM, Dynamics Marketing, Exchange Online, Exchange Online Protection, Identity Service, Mobile Device Management, Office 365 Partner Admin Center, OneDrive for Business, Parature, OneDrive for Business, Power BI for Office 365, Rights Management Service, SharePoint Online, SHD Admin, Skype for Business, Social Engagement, and Yammer Enterprise.</span></span>

## <a name="the-fundamentals"></a><span data-ttu-id="96db9-111">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="96db9-111">The fundamentals</span></span>

<span data-ttu-id="96db9-112">URL-адрес API включает идентификатор клиента, ограничивающий область действия операций одним клиентом:</span><span class="sxs-lookup"><span data-stu-id="96db9-112">The root URL of the API includes a tenant identifier that scopes the operations to a single tenant:</span></span>

```http
https://manage.office.com/api/v1.0/{tenant_identifier}/ServiceComms/{operation}
```

<span data-ttu-id="96db9-113">**API сообщений о службах Office 365** — это служба REST, позволяющая разрабатывать решения на любом языке и в любой среде внешнего размещения, поддерживающей сертификаты HTTPS и X.509.</span><span class="sxs-lookup"><span data-stu-id="96db9-113">The **Office 365 Service Communications API** is a REST service that allows you to develop solutions using any web language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="96db9-114">Этот API использует службу **Microsoft Azure Active Directory** и протокол **OAuth2** для проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="96db9-114">The API relies on **Microsoft Azure Active Directory** and the **OAuth2** protocol for authentication and authorization.</span></span> <span data-ttu-id="96db9-115">Чтобы получить доступ к API из приложения, необходимо сначала зарегистрировать его в Azure AD и задать подходящую область разрешений.</span><span class="sxs-lookup"><span data-stu-id="96db9-115">To access the API from your application, you'll need to first register it in Azure AD and configure it with permissions at the appropriate scope.</span></span> <span data-ttu-id="96db9-116">Благодаря этому приложение сможет запрашивать маркеры доступа OAuth2, необходимые для вызова API.</span><span class="sxs-lookup"><span data-stu-id="96db9-116">This will enable your application to request OAuth2 access tokens necessary for calling the API.</span></span> <span data-ttu-id="96db9-117">Дополнительные сведения о регистрации и настройке приложения в Azure AD см. в статье [Начало работы с API управления Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="96db9-117">You can find more information about registering and configuring an application in Azure AD at [Office 365 Management APIs getting started](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="96db9-118">Для всех запросов к API необходим заголовок Authorization HTTP с действительным маркером доступа JWT OAuth2, полученным из Azure AD и содержащим утверждение **ServiceHealth.Read**. А идентификатор клиента должен быть таким же, как в корневом URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="96db9-118">All API requests require an Authorization HTTP header that has a valid OAuth2 JWT access token obtained from Azure AD that contains the **ServiceHealth.Read** claim; and the tenant identifier must match the tenant identifier in the root URL.</span></span>

```json
Authorization: Bearer {OAuth2 token}
```

<span data-ttu-id="96db9-119">**Заголовки запросов**</span><span class="sxs-lookup"><span data-stu-id="96db9-119">**Request headers**</span></span>

<span data-ttu-id="96db9-120">Ниже показаны поддерживаемые заголовки запросов для всех операций API сообщений о службах Office 365.</span><span class="sxs-lookup"><span data-stu-id="96db9-120">These are the supported request headers for all Office 365 Service Communications API operations.</span></span>

|<span data-ttu-id="96db9-121">Заголовок</span><span class="sxs-lookup"><span data-stu-id="96db9-121">Header</span></span>|<span data-ttu-id="96db9-122">Описание</span><span class="sxs-lookup"><span data-stu-id="96db9-122">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="96db9-123">**Accept (необязательный)**</span><span class="sxs-lookup"><span data-stu-id="96db9-123">**Accept (Optional)**</span></span>|<span data-ttu-id="96db9-124">Ниже показаны допустимые представления отклика.</span><span class="sxs-lookup"><span data-stu-id="96db9-124">The following are acceptable representations for the response:</span></span><br/><span data-ttu-id="96db9-125">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="96db9-125">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="96db9-126">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="96db9-126">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="96db9-127">**application/json;odata.metadata=none** [используется по умолчанию, если заголовок не указан]</span><span class="sxs-lookup"><span data-stu-id="96db9-127">[The default if header not specified] **application/json;odata.metadata=none**</span></span>|
|<span data-ttu-id="96db9-128">**Authorization (обязательный)**</span><span class="sxs-lookup"><span data-stu-id="96db9-128">**Authorization (Required)**</span></span>|<span data-ttu-id="96db9-129">Маркер авторизации (токен носителя JWT Azure AD) для запроса.</span><span class="sxs-lookup"><span data-stu-id="96db9-129">Authorization token (Bearer JWT Azure AD Token) for the request.</span></span>|


<br/>

<span data-ttu-id="96db9-130">**Заголовки откликов**</span><span class="sxs-lookup"><span data-stu-id="96db9-130">**Response headers**</span></span>

<span data-ttu-id="96db9-131">Ниже показаны заголовки откликов, возвращаемые для всех операций API сообщений о службах Office 365.</span><span class="sxs-lookup"><span data-stu-id="96db9-131">These are the response headers returned for all Office 365 Service Communications API operations:</span></span>

|<span data-ttu-id="96db9-132">Заголовок</span><span class="sxs-lookup"><span data-stu-id="96db9-132">Header</span></span>|<span data-ttu-id="96db9-133">Описание</span><span class="sxs-lookup"><span data-stu-id="96db9-133">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="96db9-134">**Content-Length**</span><span class="sxs-lookup"><span data-stu-id="96db9-134">**Content-Length**</span></span>|<span data-ttu-id="96db9-135">Длина основного текста отклика.</span><span class="sxs-lookup"><span data-stu-id="96db9-135">The length of the response body.</span></span>|
|<span data-ttu-id="96db9-136">**Content-Type**</span><span class="sxs-lookup"><span data-stu-id="96db9-136">**Content-Type**</span></span>|<span data-ttu-id="96db9-137">Представление отклика:</span><span class="sxs-lookup"><span data-stu-id="96db9-137">Representation of the response:</span></span><br/><span data-ttu-id="96db9-138">**application/json**</span><span class="sxs-lookup"><span data-stu-id="96db9-138">**application/json**</span></span><br/><span data-ttu-id="96db9-139">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="96db9-139">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="96db9-140">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="96db9-140">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="96db9-141">**application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="96db9-141">**application/json;odata.metadata=none**</span></span><br/><span data-ttu-id="96db9-142">**odata.streaming=true**</span><span class="sxs-lookup"><span data-stu-id="96db9-142">**odata.streaming=true**</span></span>|
|<span data-ttu-id="96db9-143">**Cache-Control**</span><span class="sxs-lookup"><span data-stu-id="96db9-143">**Cache-Control**</span></span>|<span data-ttu-id="96db9-144">Используется для указания директив, которым должны подчиняться все механизмы кэширования в цепочке запросов и откликов.</span><span class="sxs-lookup"><span data-stu-id="96db9-144">Used to specify directives that all caching mechanisms along the request/response chain must obey.</span></span>|
|<span data-ttu-id="96db9-145">**Pragma**</span><span class="sxs-lookup"><span data-stu-id="96db9-145">**Pragma**</span></span>|<span data-ttu-id="96db9-146">Поведение для конкретных реализаций.</span><span class="sxs-lookup"><span data-stu-id="96db9-146">Implementation-specific behaviors.</span></span>|
|<span data-ttu-id="96db9-147">**Expires**</span><span class="sxs-lookup"><span data-stu-id="96db9-147">**Expires**</span></span>|<span data-ttu-id="96db9-148">Указывает, когда клиент должен сделать ресурс устаревшим.</span><span class="sxs-lookup"><span data-stu-id="96db9-148">When the client should make the resource expire.</span></span>|
|<span data-ttu-id="96db9-149">**X-Activity-Id**</span><span class="sxs-lookup"><span data-stu-id="96db9-149">**X-Activity-Id**</span></span>|<span data-ttu-id="96db9-150">Созданный сервером идентификатор действия.</span><span class="sxs-lookup"><span data-stu-id="96db9-150">The server-generated activity Id.</span></span>|
|<span data-ttu-id="96db9-151">**OData-Version**</span><span class="sxs-lookup"><span data-stu-id="96db9-151">**OData-Version**</span></span>|<span data-ttu-id="96db9-152">Поддерживаемая версия OData (4.0).</span><span class="sxs-lookup"><span data-stu-id="96db9-152">The supported OData Version (4.0).</span></span>|
|<span data-ttu-id="96db9-153">**Date**</span><span class="sxs-lookup"><span data-stu-id="96db9-153">**Date**</span></span>|<span data-ttu-id="96db9-154">Дата отправки отклика с сервера (в формате UTC).</span><span class="sxs-lookup"><span data-stu-id="96db9-154">The date in UTC when the response was sent from the server.</span></span>|
|<span data-ttu-id="96db9-155">**X-Time-Taken**</span><span class="sxs-lookup"><span data-stu-id="96db9-155">**X-Time-Taken**</span></span>|<span data-ttu-id="96db9-156">Время, затраченное на создание отклика (мс).</span><span class="sxs-lookup"><span data-stu-id="96db9-156">The time it took to generate the response (ms).</span></span>|
|<span data-ttu-id="96db9-157">**X-Instance-Name**</span><span class="sxs-lookup"><span data-stu-id="96db9-157">**X-Instance-Name**</span></span>|<span data-ttu-id="96db9-158">Идентификатор экземпляра Azure, используемого для создания отклика (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="96db9-158">The identifier of the Azure instance used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="96db9-159">**Server**</span><span class="sxs-lookup"><span data-stu-id="96db9-159">**Server**</span></span>|<span data-ttu-id="96db9-160">Сервер, используемый для создания отклика (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="96db9-160">The server used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="96db9-161">**X-ASPNET-Version**</span><span class="sxs-lookup"><span data-stu-id="96db9-161">**X-ASPNET-Version**</span></span>|<span data-ttu-id="96db9-162">Версия ASP.Net, используемая на сервере, который создал отклик (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="96db9-162">The version of ASP.Net used by the server that generated the response (for debugging purposes).</span></span>|
|<span data-ttu-id="96db9-163">**X-Powered-By**</span><span class="sxs-lookup"><span data-stu-id="96db9-163">**X-Powered-By**</span></span>|<span data-ttu-id="96db9-164">Технологии, используемые на сервере, который создал отклик (в целях отладки).</span><span class="sxs-lookup"><span data-stu-id="96db9-164">The technologies used in the server that generated the response (for debugging purposes).</span></span>|

<br/>

<span data-ttu-id="96db9-165">Ниже представлены операции API сообщений о службах Office 365.</span><span class="sxs-lookup"><span data-stu-id="96db9-165">Following are the Office 365 Service Communications API operations.</span></span>


## <a name="get-services"></a><span data-ttu-id="96db9-166">Получение служб</span><span class="sxs-lookup"><span data-stu-id="96db9-166">Get Services</span></span>

<span data-ttu-id="96db9-167">Возвращает список подписанных служб.</span><span class="sxs-lookup"><span data-stu-id="96db9-167">Returns the list of subscribed services.</span></span>

||<span data-ttu-id="96db9-168">Служба</span><span class="sxs-lookup"><span data-stu-id="96db9-168">Service</span></span>|<span data-ttu-id="96db9-169">Описание</span><span class="sxs-lookup"><span data-stu-id="96db9-169">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="96db9-170">**Путь**</span><span class="sxs-lookup"><span data-stu-id="96db9-170">**Path**</span></span>| `/Services`||
|<span data-ttu-id="96db9-171">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="96db9-171">**Query-option**</span></span>|<span data-ttu-id="96db9-172">$select</span><span class="sxs-lookup"><span data-stu-id="96db9-172">$select</span></span>|<span data-ttu-id="96db9-173">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="96db9-173">Pick a subset of properties.</span></span>|
|<span data-ttu-id="96db9-174">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="96db9-174">**Response**</span></span>|<span data-ttu-id="96db9-175">Список объектов Service</span><span class="sxs-lookup"><span data-stu-id="96db9-175">List of "Service" entities</span></span>|<span data-ttu-id="96db9-176">Объект Service содержит свойства Id (String), DisplayName (String) и FeatureNames (список String).</span><span class="sxs-lookup"><span data-stu-id="96db9-176">"Service" entity contains "Id" (String), "DisplayName" (String), and "FeatureNames" (list of Strings).</span></span>|

#### <a name="sample-request"></a><span data-ttu-id="96db9-177">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="96db9-177">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Services 
Authorization: Bearer {AAD_Bearer_JWT_Token}

```

#### <a name="sample-response"></a><span data-ttu-id="96db9-178">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="96db9-178">Sample response</span></span>

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


## <a name="get-current-status"></a><span data-ttu-id="96db9-179">Получение текущего состояния</span><span class="sxs-lookup"><span data-stu-id="96db9-179">Get Current Status</span></span>

<span data-ttu-id="96db9-180">Возвращает состояние службы за предыдущие 24 часа.</span><span class="sxs-lookup"><span data-stu-id="96db9-180">Returns the status of the service over the previous 24 hours.</span></span>

||<span data-ttu-id="96db9-181">Служба</span><span class="sxs-lookup"><span data-stu-id="96db9-181">Service</span></span>|<span data-ttu-id="96db9-182">Описание</span><span class="sxs-lookup"><span data-stu-id="96db9-182">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="96db9-183">**Путь**</span><span class="sxs-lookup"><span data-stu-id="96db9-183">**Path**</span></span>| `/CurrentStatus`||
|<span data-ttu-id="96db9-184">**Фильтр**</span><span class="sxs-lookup"><span data-stu-id="96db9-184">**Filter**</span></span>|<span data-ttu-id="96db9-185">Workload</span><span class="sxs-lookup"><span data-stu-id="96db9-185">Workload</span></span>|<span data-ttu-id="96db9-186">Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="96db9-186">Filter by workload (String, default: all).</span></span>|
|<span data-ttu-id="96db9-187">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="96db9-187">**Query-option**</span></span>|<span data-ttu-id="96db9-188">$select</span><span class="sxs-lookup"><span data-stu-id="96db9-188">$select</span></span>|<span data-ttu-id="96db9-189">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="96db9-189">Pick a subset of properties.</span></span>|
|<span data-ttu-id="96db9-190">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="96db9-190">**Response**</span></span>|<span data-ttu-id="96db9-191">Список объектов WorkloadStatus.</span><span class="sxs-lookup"><span data-stu-id="96db9-191">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="96db9-192">Объект WorkloadStatus содержит свойства Id (String), Workload (String), StatusTime (DateTimeOffset), WorkloadDisplayName (String), Status (String), IncidentIds (список String) и FeatureGroupStatusCollection (список объектов FeatureStatus).</span><span class="sxs-lookup"><span data-stu-id="96db9-192">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="96db9-193">Объект FeatureStatus содержит свойства Feature (String), FeatureGroupDisplayName (String) и FeatureStatus (String).</span><span class="sxs-lookup"><span data-stu-id="96db9-193">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|

#### <a name="sample-request"></a><span data-ttu-id="96db9-194">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="96db9-194">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/CurrentStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a><span data-ttu-id="96db9-195">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="96db9-195">Sample response</span></span>

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


## <a name="get-historical-status"></a><span data-ttu-id="96db9-196">Получение сведений об изменении состояния</span><span class="sxs-lookup"><span data-stu-id="96db9-196">Get Historical Status</span></span>

<span data-ttu-id="96db9-197">Возвращает сведения об изменении состояния службы по дням за определенный диапазон времени.</span><span class="sxs-lookup"><span data-stu-id="96db9-197">Returns the historical status of the service, by day, over a certain time range.</span></span>

||<span data-ttu-id="96db9-198">Служба</span><span class="sxs-lookup"><span data-stu-id="96db9-198">Service</span></span>|<span data-ttu-id="96db9-199">Описание</span><span class="sxs-lookup"><span data-stu-id="96db9-199">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="96db9-200">**Путь**</span><span class="sxs-lookup"><span data-stu-id="96db9-200">**Path**</span></span>| `/HistoricalStatus`||
|<span data-ttu-id="96db9-201">**Фильтры**</span><span class="sxs-lookup"><span data-stu-id="96db9-201">**Filters**</span></span>|<span data-ttu-id="96db9-202">Workload</span><span class="sxs-lookup"><span data-stu-id="96db9-202">Workload</span></span>|<span data-ttu-id="96db9-203">Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="96db9-203">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="96db9-204">StatusTime</span><span class="sxs-lookup"><span data-stu-id="96db9-204">StatusTime</span></span>|<span data-ttu-id="96db9-205">Фильтрация по дням после StatusTime (DateTimeOffset, значение по умолчанию: 7 дней для ge CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="96db9-205">Filter by days greater than StatusTime (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
|<span data-ttu-id="96db9-206">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="96db9-206">**Query-option**</span></span>|<span data-ttu-id="96db9-207">$select</span><span class="sxs-lookup"><span data-stu-id="96db9-207">$select</span></span>|<span data-ttu-id="96db9-208">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="96db9-208">Pick a subset of properties.</span></span>|
|<span data-ttu-id="96db9-209">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="96db9-209">**Response**</span></span>|<span data-ttu-id="96db9-210">Список объектов WorkloadStatus.</span><span class="sxs-lookup"><span data-stu-id="96db9-210">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="96db9-211">Объект WorkloadStatus содержит свойства Id (String), Workload (String), StatusTime (DateTimeOffset), WorkloadDisplayName (String), Status (String), IncidentIds (список String) и FeatureGroupStatusCollection (список объектов FeatureStatus).</span><span class="sxs-lookup"><span data-stu-id="96db9-211">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="96db9-212">Объект FeatureStatus содержит свойства Feature (String), FeatureGroupDisplayName (String) и FeatureStatus (String).</span><span class="sxs-lookup"><span data-stu-id="96db9-212">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|

#### <a name="sample-request"></a><span data-ttu-id="96db9-213">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="96db9-213">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/HistoricalStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a><span data-ttu-id="96db9-214">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="96db9-214">Sample response</span></span>

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


## <a name="get-messages"></a><span data-ttu-id="96db9-215">Получение сообщений</span><span class="sxs-lookup"><span data-stu-id="96db9-215">Get Messages</span></span>

<span data-ttu-id="96db9-216">Возвращает сообщения о службе за определенный диапазон времени.</span><span class="sxs-lookup"><span data-stu-id="96db9-216">Returns the messages about the service over a certain time range.</span></span> <span data-ttu-id="96db9-217">Используйте фильтр по типу, чтобы просмотреть сообщения об инцидентах обслуживания, плановом обслуживании или из Центра сообщений.</span><span class="sxs-lookup"><span data-stu-id="96db9-217">Use the type filter to filter for "Service Incident", "Planned Maintenance", or "Message Center" messages.</span></span>

||<span data-ttu-id="96db9-218">Служба</span><span class="sxs-lookup"><span data-stu-id="96db9-218">Service</span></span>|<span data-ttu-id="96db9-219">Описание</span><span class="sxs-lookup"><span data-stu-id="96db9-219">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="96db9-220">**Путь**</span><span class="sxs-lookup"><span data-stu-id="96db9-220">**Path**</span></span>| `/Messages`||
|<span data-ttu-id="96db9-221">**Фильтры**</span><span class="sxs-lookup"><span data-stu-id="96db9-221">**Filters**</span></span>|<span data-ttu-id="96db9-222">Workload</span><span class="sxs-lookup"><span data-stu-id="96db9-222">Workload</span></span>|<span data-ttu-id="96db9-223">Фильтрация по рабочей нагрузке (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="96db9-223">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="96db9-224">StartTime</span><span class="sxs-lookup"><span data-stu-id="96db9-224">StartTime</span></span>|<span data-ttu-id="96db9-225">Фильтрация по времени начала (DateTimeOffset, значение по умолчанию: 7 дней для ge CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="96db9-225">Filter by Start Time (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
||<span data-ttu-id="96db9-226">EndTime</span><span class="sxs-lookup"><span data-stu-id="96db9-226">EndTime</span></span>|<span data-ttu-id="96db9-227">Фильтрация по времени окончания (DateTimeOffset, значение по умолчанию: le CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="96db9-227">Filter by End Time (DateTimeOffset, default: le CurrentTime).</span></span>|
||<span data-ttu-id="96db9-228">MessageType</span><span class="sxs-lookup"><span data-stu-id="96db9-228">MessageType</span></span>|<span data-ttu-id="96db9-229">Фильтрация по MessageType (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="96db9-229">Filter by MessageType (String, default: all).</span></span>|
||<span data-ttu-id="96db9-230">ID</span><span class="sxs-lookup"><span data-stu-id="96db9-230">ID</span></span>|<span data-ttu-id="96db9-231">Фильтрация по идентификатору (String, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="96db9-231">Filter by ID (String, default: all).</span></span>|
|<span data-ttu-id="96db9-232">**Параметр запроса**</span><span class="sxs-lookup"><span data-stu-id="96db9-232">**Query-option**</span></span>|<span data-ttu-id="96db9-233">$select</span><span class="sxs-lookup"><span data-stu-id="96db9-233">$select</span></span>|<span data-ttu-id="96db9-234">Выбор подмножества свойств.</span><span class="sxs-lookup"><span data-stu-id="96db9-234">Pick a subset of properties.</span></span>|
||<span data-ttu-id="96db9-235">$top</span><span class="sxs-lookup"><span data-stu-id="96db9-235">$top</span></span>|<span data-ttu-id="96db9-236">Выбор максимального количества результатов (используемое по умолчанию и максимальное значение: $top=100).</span><span class="sxs-lookup"><span data-stu-id="96db9-236">Pick the top number of results (default and max $top=100).</span></span>|
||<span data-ttu-id="96db9-237">$skip</span><span class="sxs-lookup"><span data-stu-id="96db9-237">$skip</span></span>|<span data-ttu-id="96db9-238">Пропуск определенного количества результатов (значение по умолчанию: $skip=0).</span><span class="sxs-lookup"><span data-stu-id="96db9-238">Skip number of results (default: $skip=0).</span></span>|
|<span data-ttu-id="96db9-239">**Отклик**</span><span class="sxs-lookup"><span data-stu-id="96db9-239">**Response**</span></span>|<span data-ttu-id="96db9-240">Список объектов Message.</span><span class="sxs-lookup"><span data-stu-id="96db9-240">List of "Message" entities.</span></span>|<span data-ttu-id="96db9-241">Объект Message содержит свойства Id (String), StartTime (DateTimeOffset), EndTime (DateTimeOffset), Status (String), Messages (список объектов MessageHistory), LastUpdatedTime (DateTimeOffset), Workload (String), WorkloadDisplayName (String), Feature (String), FeatureDisplayName (String), MessageType (Enum, значение по умолчанию: all).</span><span class="sxs-lookup"><span data-stu-id="96db9-241">"Message" entity contains "Id" (String), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (String), "Messages" (list of "MessageHistory" entity), "LastUpdatedTime" (DateTimeOffset), "Workload" (String), "WorkloadDisplayName" (String), "Feature" (String), "FeatureDisplayName" (String), "MessageType" (Enum, default: all).</span></span><br/><br/><span data-ttu-id="96db9-242">Объект MessageHistory содержит свойства PublishedTime (DateTimeOffset), MessageText (String).</span><span class="sxs-lookup"><span data-stu-id="96db9-242">"MessageHistory" entity contains "PublishedTime" (DateTimeOffset), "MessageText" (String).</span></span>|

#### <a name="sample-request"></a><span data-ttu-id="96db9-243">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="96db9-243">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Messages
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a><span data-ttu-id="96db9-244">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="96db9-244">Sample response</span></span>

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


## <a name="errors"></a><span data-ttu-id="96db9-245">Ошибки</span><span class="sxs-lookup"><span data-stu-id="96db9-245">Errors</span></span>

<span data-ttu-id="96db9-246">Когда служба обнаруживает ошибку, она возвращает отправителю вызова соответствующий код отклика, используя стандартный синтаксис кодов ошибок HTTP.</span><span class="sxs-lookup"><span data-stu-id="96db9-246">When the service encounters an error, it reports the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="96db9-247">Согласно [спецификации OData версии 4](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html) дополнительные сведения включены в текст запроса, вернувшего код ошибки, в виде одного объекта JSON.</span><span class="sxs-lookup"><span data-stu-id="96db9-247">As per [OData V4 specification](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="96db9-248">Ниже представлен пример полного текста ошибки JSON.</span><span class="sxs-lookup"><span data-stu-id="96db9-248">The following is an example of a full JSON error body:</span></span>


```json

{ 
    "error":{ 
        "code":"AF5000.  An internal server error occurred.",
        "message": "Retry the request." 
    } 
}

```

