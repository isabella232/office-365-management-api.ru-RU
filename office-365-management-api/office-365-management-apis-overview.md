---
ms.TocTitle: Office 365 Management APIs overview
title: Обзор API управления Office 365
description: Представляет собой единую платформу расширяемости, позволяющую пользователям и партнерам Office 365 выполнять все задачи управления, включая обеспечение отправки служебных сообщений, безопасности, соответствия требованиям, создания отчетов, а также аудита.
ms.ContentId: 4fca85f9-efa6-3b4b-b10d-a07cb31f803f
ms.topic: reference (API)
ms.date: 09/28/2016
localization_priority: Priority
ms.openlocfilehash: 88b7e590d769699ed186d7cecaf80e162d79a095
ms.sourcegitcommit: 36d0167805d24bbb3e2cf1a02d0f011270cc31cb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2020
ms.locfileid: "41263284"
---
# <a name="office-365-management-apis-overview"></a><span data-ttu-id="fd6d2-103">Обзор API управления Office 365</span><span class="sxs-lookup"><span data-stu-id="fd6d2-103">Office 365 Management APIs overview</span></span>

<span data-ttu-id="fd6d2-104">API управления Office 365 представляют собой единую платформу расширяемости, позволяющую пользователям и партнерам Office 365 выполнять все задачи управления, включая обеспечение отправки служебных сообщений, безопасности, соответствия требованиям, создания отчетов, а также аудита.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-104">The Office 365 Management APIs provide a single extensibility platform for all Office 365 customers' and partners' management tasks, including service communications, security, compliance, reporting, and auditing.</span></span> <span data-ttu-id="fd6d2-105">Все интерфейсы API управления Office 365 соответствуют по исполнению и особенностям внедрения текущему набору интерфейсов REST API Office 365 и позволяют реализовать стандартные подходы, такие как использование OAuth 2, OData 4 и JSON.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-105">All of the Office 365 Management APIs are consistent in design and implementation with the current suite of Office 365 REST APIs, using common industry-standard approaches, including OAuth v2, OData v4, and JSON.</span></span> <span data-ttu-id="fd6d2-106">Как и в случае других API Office 365, приложения регистрируются в Azure Active Directory, что позволяет разработчикам обеспечить единообразную аутентификацию и авторизацию для своих приложений.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-106">Like the other Office 365 APIs, applications are registered in Azure Active Directory, giving developers a consistent way to authenticate and authorize their apps.</span></span>

<span data-ttu-id="fd6d2-107">Если у вас есть вопросы об API управления Office 365, задайте их на сайте [Stack Overflow](http://stackoverflow.com/tags/office365), добавив тег [office365].</span><span class="sxs-lookup"><span data-stu-id="fd6d2-107">If you have questions about the Office 365 Management APIs, post your question on [Stack Overflow](http://stackoverflow.com/tags/office365), using the [office365] tag.</span></span>

## <a name="office-365-service-communications-api-preview"></a><span data-ttu-id="fd6d2-108">API служебных сообщений Office 365 (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="fd6d2-108">Office 365 Service Communications API (preview)</span></span>

<span data-ttu-id="fd6d2-109">Интерфейс API служебных сообщений Office 365 выпущен в режиме предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-109">The Office 365 Service Communications API has been released in preview mode.</span></span> <span data-ttu-id="fd6d2-110">Он замещает предыдущую версию API служебных сообщений Office 365 и предоставляет сведения о работоспособности службы партнерам и администраторам клиента.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-110">It replaces the Office 365 Service Communications API to provide service health information to tenant administrators and partners.</span></span> <span data-ttu-id="fd6d2-111">В отличие от предыдущей версии, новый API служебных сообщений обеспечивает целостный подход к использованию, так как интерфейсы REST API встраиваются единообразным способом (это касается именования URL-адресов, формата данных и аутентификации).</span><span class="sxs-lookup"><span data-stu-id="fd6d2-111">Unlike the previous version, the new Service Communications API delivers a cohesive platform experience, with REST APIs built in a consistent fashion including URL naming, data format, and authentication.</span></span>

<span data-ttu-id="fd6d2-112">Новые возможности добавляются только в новые версии API, что должно способствовать раннему внедрению пользователями устаревших версий.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-112">New features are only added to the new version of the API, encouraging early adoption by legacy customers.</span></span> <span data-ttu-id="fd6d2-113">После общего извещения о новом API служебных сообщений Office 365 начался период объявления предыдущей версии этого интерфейса устаревшей.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-113">When the General Announcement of Office 365 Service Communications API was made, the older version of the Service Communications API began a period of deprecation.</span></span> 

<span data-ttu-id="fd6d2-114">Для ознакомления с операциями см. статью [Справочник по API служебных сообщений Office 365 (предварительная версия)](office-365-service-communications-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="fd6d2-114">For the operations reference, see [Office 365 Service Communications API reference (preview)](office-365-service-communications-api-reference.md).</span></span>


## <a name="office-365-management-activity-api"></a><span data-ttu-id="fd6d2-115">API действий управления Office 365</span><span class="sxs-lookup"><span data-stu-id="fd6d2-115">Office 365 Management Activity API</span></span>

<span data-ttu-id="fd6d2-116">API действий управления Office 365 обеспечивает получение информации о различных действиях и событиях, касающихся пользователей, администраторов, систем и политик, из отчетов о действиях касательно Office 365 и Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-116">The Office 365 Management Activity API provides information about various user, admin, system, and policy actions and events from Office 365 and Azure Active Directory activity logs.</span></span> <span data-ttu-id="fd6d2-117">Партнеры и пользователи могут с учетом этой информации создавать новые и улучшать существующие операции, средства обеспечения безопасности и решения для мониторинга соответствия требованиям в предприятии.</span><span class="sxs-lookup"><span data-stu-id="fd6d2-117">Customers and partners can use this information to create new or enhance existing operations, security, and compliance-monitoring solutions for the enterprise.</span></span> 

<span data-ttu-id="fd6d2-118">Для ознакомления с операциями см. статью [Справочник по API действий управления Office 365](office-365-management-activity-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="fd6d2-118">For the operations reference, see [Office 365 Management Activity API reference](office-365-management-activity-api-reference.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd6d2-119">См. также</span><span class="sxs-lookup"><span data-stu-id="fd6d2-119">See also</span></span>

- [<span data-ttu-id="fd6d2-120">Начало работы с API управления Office 365</span><span class="sxs-lookup"><span data-stu-id="fd6d2-120">Get started with Office 365 Management APIs</span></span>](get-started-with-office-365-management-apis.md)
- [<span data-ttu-id="fd6d2-121">Схема API действий управления Office 365</span><span class="sxs-lookup"><span data-stu-id="fd6d2-121">Office 365 Management Activity API schema</span></span>](office-365-management-activity-api-schema.md)
- [<span data-ttu-id="fd6d2-122">Устранение неполадок, связанных с API действий управления Office 365</span><span class="sxs-lookup"><span data-stu-id="fd6d2-122">Troubleshooting the Office 365 Management Activity API</span></span>](troubleshooting-the-office-365-management-activity-api.md)
- [<span data-ttu-id="fd6d2-123">Интерфейсы REST API Office 365</span><span class="sxs-lookup"><span data-stu-id="fd6d2-123">Office 365 REST APIs</span></span>](https://docs.microsoft.com/previous-versions/office/office-365-api/how-to/platform-development-overview)

