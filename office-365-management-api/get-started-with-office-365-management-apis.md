---
ms.technology: o365-service-communications
ms.TocTitle: Get started with Office 365 Management APIs
title: Начало работы с API управления Office 365
description: API используют Azure AD, чтобы предоставлять службы проверки подлинности, с помощью которых вы можете давать приложениям права доступа к этим службам.
ms.ContentId: 74137c9a-29e0-b588-6122-26f4d2c5e3fc
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: d11644a4a9985096c14ad4ae265471159243b65b
ms.sourcegitcommit: ec60dbd5990cfc61b8c000b423e7ade25fa613a8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "48397449"
---
# <a name="get-started-with-office-365-management-apis"></a><span data-ttu-id="0c480-103">Начало работы с API управления Office 365</span><span class="sxs-lookup"><span data-stu-id="0c480-103">Get started with Office 365 Management APIs</span></span>

<span data-ttu-id="0c480-104">При создании приложения, которое нуждается в доступе к таким защищенным службам, как интерфейсы API управления Office 365, вам необходимо обеспечить возможность сообщать службе о наличии у приложения права на доступ к ней.</span><span class="sxs-lookup"><span data-stu-id="0c480-104">When you create an application that needs access to secured services like the Office 365 Management APIs, you need to provide a way to let the service know if your application has rights to access it.</span></span> <span data-ttu-id="0c480-105">API управления Office 365 используют Azure AD, чтобы предоставлять службы проверки подлинности, с помощью которых вы можете давать приложениям права доступа к этим службам.</span><span class="sxs-lookup"><span data-stu-id="0c480-105">The Office 365 Management APIs use Azure AD to provide authentication services that you can use to grant rights for your application to access them.</span></span> 

<span data-ttu-id="0c480-106">Этот процесс делится на четыре основных этапа.</span><span class="sxs-lookup"><span data-stu-id="0c480-106">There are four key steps:</span></span>

1. <span data-ttu-id="0c480-107">**Регистрация приложения в Azure AD.**</span><span class="sxs-lookup"><span data-stu-id="0c480-107">**Register your application in Azure AD**.</span></span> <span data-ttu-id="0c480-108">Чтобы ваше приложение имело доступ к API управления Office 365, вам необходимо зарегистрировать приложение в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0c480-108">To allow your application access to the Office 365 Management APIs, you need to register your application in Azure AD.</span></span> <span data-ttu-id="0c480-109">Это позволяет создать удостоверение для приложения b задать уровни разрешений, необходимые ему для доступа к API.</span><span class="sxs-lookup"><span data-stu-id="0c480-109">This allows you to establish an identity for your application and specify the permission levels it needs to access the APIs.</span></span>
    
2. <span data-ttu-id="0c480-110">**Получение согласия администратора клиента Office 365.**</span><span class="sxs-lookup"><span data-stu-id="0c480-110">**Get Office 365 tenant admin consent**.</span></span> <span data-ttu-id="0c480-111">Администратор клиента Office 365 должен явно дать согласие, чтобы приложение могло получать доступ к данным клиента при помощи API управления Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-111">An Office 365 tenant admin must explicitly grant consent to allow your application to access their tenant data by means of the Office 365 Management APIs.</span></span> <span data-ttu-id="0c480-112">Процесс получения согласия проходит в браузере, поэтому администратору клиента необходимо войти в **пользовательский интерфейс согласия Azure AD** и просмотреть разрешения доступа, которые запрашивает приложение, а затем подтвердить или отклонить запрос.</span><span class="sxs-lookup"><span data-stu-id="0c480-112">The consent process is a browser-based experience that requires the tenant admin to sign in to the **Azure AD consent UI** and review the access permissions that your application is requesting, and then either grant or deny the request.</span></span> <span data-ttu-id="0c480-113">После предоставления согласия пользовательский интерфейс перенаправляет пользователя обратно в приложение с помощью кода авторизации в URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="0c480-113">After consent is granted, the UI redirects the user back to your application with an authorization code in the URL.</span></span> <span data-ttu-id="0c480-114">Приложение отправляет вызов между службами к Azure AD, чтобы обменять этот код авторизации на маркер доступа, содержащий сведения об администраторе клиента и вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="0c480-114">Your application makes a service-to-service call to Azure AD to exchange this authorization code for an access token, which contains information about both the tenant admin and your application.</span></span> <span data-ttu-id="0c480-115">ИД клиента необходимо извлечь из маркера доступа и сохранить для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="0c480-115">The tenant ID must be extracted from the access token and stored for future use.</span></span>
    
3. <span data-ttu-id="0c480-116">**Запросы маркеров доступа из Azure AD.**</span><span class="sxs-lookup"><span data-stu-id="0c480-116">**Request access tokens from Azure AD**.</span></span> <span data-ttu-id="0c480-117">Используя учетные данные приложения, настроенные в Azure AD, приложение регулярно запрашивает дополнительные маркеры доступа для согласившегося клиента, а дальнейшее участие администратора клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="0c480-117">Using your application's credentials as configured in Azure AD, your application requests additional access tokens for a consented tenant on an ongoing basis, without the need for further tenant admin interaction.</span></span> <span data-ttu-id="0c480-118">Эти маркеры доступа называются маркерами только для приложений, потому что они не содержат сведения об администраторе клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-118">These access tokens are called app-only tokens because they do not include information about the tenant admin.</span></span>
    
4. <span data-ttu-id="0c480-119">**Вызов API управления Office 365.**</span><span class="sxs-lookup"><span data-stu-id="0c480-119">**Call the Office 365 Management APIs**.</span></span> <span data-ttu-id="0c480-120">Маркеры доступа только для приложений передаются интерфейсам API управления Office 365, чтобы выполнить проверку подлинности и авторизацию приложения.</span><span class="sxs-lookup"><span data-stu-id="0c480-120">The app-only access tokens are passed to the Office 365 Management APIs to authenticate and authorize your application.</span></span>
    
<span data-ttu-id="0c480-121">На приведенной ниже схеме показана последовательность предоставления согласия и запросов маркеров доступа.</span><span class="sxs-lookup"><span data-stu-id="0c480-121">The following diagram shows the sequence of consent and access token requests.</span></span>

![Поток автоматизации запуска API-интерфейсов управления](images/authorization-flow.png)

> [!IMPORTANT]
> <span data-ttu-id="0c480-123">Чтобы получить доступ к данным с помощью API действий управления Office 365, требуется включить ведение единого журнала аудита для организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-123">Before you can access data through the Office 365 Management Activity API, you must enable unified audit logging for your Office 365 organization.</span></span> <span data-ttu-id="0c480-124">Это выполняется путем включения журнала аудита Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-124">You do this by turning on the Office 365 audit log.</span></span> <span data-ttu-id="0c480-125">Инструкции см. в статье [Включение и отключение поиска в журнале аудита Office 365](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).</span><span class="sxs-lookup"><span data-stu-id="0c480-125">For instructions, see [Turn Office 365 audit log search on or off](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).</span></span> <br/><br/><span data-ttu-id="0c480-126">Включение ведения единого журнала аудита не требуется, если вы используете только API служебных сообщений Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-126">Enabling unified audit logging isn't required if you're only using the Office 365 Service Communications API.</span></span>

## <a name="register-your-application-in-azure-ad"></a><span data-ttu-id="0c480-127">Регистрация приложения в Azure AD</span><span class="sxs-lookup"><span data-stu-id="0c480-127">Register your application in Azure AD</span></span>

<span data-ttu-id="0c480-128">API управления Office 365 используют Azure AD для обеспечения безопасной аутентификации данных клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-128">The Office 365 Management APIs use Azure AD to provide secure authentication to Office 365 tenant data.</span></span> <span data-ttu-id="0c480-129">Чтобы получить доступ к интерфейсам API управления Office 365, необходимо зарегистрировать приложение в Azure AD, а в рамках настройки указать уровни разрешений, необходимые приложению для доступа к API.</span><span class="sxs-lookup"><span data-stu-id="0c480-129">To access the Office 365 Management APIs, you need to register your app in Azure AD, and as part of the configuration, you will specify the permission levels your app needs to access the APIs.</span></span>


### <a name="prerequisites"></a><span data-ttu-id="0c480-130">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="0c480-130">Prerequisites</span></span>

<span data-ttu-id="0c480-131">Чтобы зарегистрировать приложение в Azure AD, вам необходимы подписка на Office 365 и подписка Azure, связанная с подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-131">To register your app in Azure AD, you need a subscription to Office 365 and a subscription to Azure that has been associated with your Office 365 subscription.</span></span> <span data-ttu-id="0c480-132">Для начала вы можете использовать пробные подписки на Office 365 и Azure.</span><span class="sxs-lookup"><span data-stu-id="0c480-132">You can use trial subscriptions to both Office 365 and Azure to get started.</span></span> <span data-ttu-id="0c480-133">Дополнительные сведения см. в статье [Вопросы и ответы о программе для разработчиков Office 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="0c480-133">For more details, see [Welcome to the Office 365 Developer Program](https://docs.microsoft.com/office/developer-program/office-365-developer-program).</span></span>


### <a name="use-the-azure-management-portal-to-register-your-application-in-azure-ad"></a><span data-ttu-id="0c480-134">Регистрация приложения в Azure AD с помощью портала управления Azure</span><span class="sxs-lookup"><span data-stu-id="0c480-134">Use the Azure Management Portal to register your application in Azure AD</span></span>

<span data-ttu-id="0c480-135">Подготовив клиент Майкрософт с подходящими подписками, вы можете зарегистрировать приложение в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0c480-135">After you have a Microsoft tenant with the proper subscriptions, you can register your application in Azure AD.</span></span>

1. <span data-ttu-id="0c480-136">Войдите на [портал управления Azure](https://manage.windowsazure.com/), используя учетные данные клиента, у которого есть нужная вам подписка на Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-136">Sign into the [Azure management portal](https://manage.windowsazure.com/), using the credential of your Microsoft tenant that has the subscription to Office 365 you wish to use.</span></span> <span data-ttu-id="0c480-137">Вы также можете получить доступ к порталу управления Azure по ссылке в левой области навигации на [портале администрирования Office](https://portal.office.com/).</span><span class="sxs-lookup"><span data-stu-id="0c480-137">You can also access the Azure Management Portal via a link that appears in the left navigation pane in the [Office admin portal](https://portal.office.com/).</span></span>
    
2. <span data-ttu-id="0c480-138">В области навигации слева выберите Active Directory (1).</span><span class="sxs-lookup"><span data-stu-id="0c480-138">In the left navigation panel, choose Active Directory (1).</span></span> <span data-ttu-id="0c480-139">Убедитесь, что выбрана вкладка "Каталог" (2), и выберите имя каталога (3).</span><span class="sxs-lookup"><span data-stu-id="0c480-139">Make sure the Directory tab (2) is selected, and then select the directory name (3).</span></span>
    
   ![Страница регистрации Office 365](images/o365-sign-up-page.png)
    
    
3. <span data-ttu-id="0c480-141">На странице каталога выберите **Приложения**.</span><span class="sxs-lookup"><span data-stu-id="0c480-141">On the directory page, select **Applications**.</span></span> <span data-ttu-id="0c480-142">В Azure AD появится список приложений, установленных в клиенте.</span><span class="sxs-lookup"><span data-stu-id="0c480-142">Azure AD displays a list of the applications currently installed in your tenancy.</span></span>
    
4. <span data-ttu-id="0c480-143">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="0c480-143">Choose **Add**.</span></span>
    
   ![Страница администрирования Office 365](images/o365-admin-page.png)
    
    
5. <span data-ttu-id="0c480-145">Нажмите **Добавить приложение, разрабатываемое моей организацией**.</span><span class="sxs-lookup"><span data-stu-id="0c480-145">Select **Add an application my organization is developing**.</span></span>
    
6. <span data-ttu-id="0c480-146">Введите **имя** приложения и выберите **тип** "Веб-приложение и/или веб-API".</span><span class="sxs-lookup"><span data-stu-id="0c480-146">Enter the **NAME** of your application and specify the **Type** as WEB APPLICATION AND/OR WEB API.</span></span>
    
7. <span data-ttu-id="0c480-147">Укажите соответствующие свойства приложения:</span><span class="sxs-lookup"><span data-stu-id="0c480-147">Enter the appropriate App properties:</span></span>
    
   - <span data-ttu-id="0c480-148">**URL-адрес для входа.**</span><span class="sxs-lookup"><span data-stu-id="0c480-148">**SIGN-ON URL**.</span></span> <span data-ttu-id="0c480-149">URL-адрес, по которому пользователи могут входить и использовать приложение.</span><span class="sxs-lookup"><span data-stu-id="0c480-149">The URL where users can sign in and use your app.</span></span> <span data-ttu-id="0c480-150">При необходимости его можно изменить позже.</span><span class="sxs-lookup"><span data-stu-id="0c480-150">You can change this later as needed.</span></span>
    
   - <span data-ttu-id="0c480-151">**URI кода приложения.**</span><span class="sxs-lookup"><span data-stu-id="0c480-151">**APP ID URI**.</span></span> <span data-ttu-id="0c480-152">Универсальный код ресурса (URI), используемый в качестве уникального логического идентификатора приложения.</span><span class="sxs-lookup"><span data-stu-id="0c480-152">The URI used as a unique logical identifier for your app.</span></span> <span data-ttu-id="0c480-153">URI должен относиться к проверенному личному домену внешнего пользователя, чтобы предоставить приложению доступ к его данным в Windows Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0c480-153">The URI must be in a verified custom domain for an external user to grant your app access to their data in Windows Azure AD.</span></span> <span data-ttu-id="0c480-154">Например, если ваш клиент Майкрософт — **contoso.onmicrosoft.com**, то URI кода приложения будет **https://app.contoso.onmicrosoft.com**.</span><span class="sxs-lookup"><span data-stu-id="0c480-154">For example, if your Microsoft tenant is **contoso.onmicrosoft.com**, the APP ID URI could be **https://app.contoso.onmicrosoft.com**.</span></span>
    
8. <span data-ttu-id="0c480-155">Теперь ваше приложение зарегистрировано в Azure AD, и ему назначен идентификатор клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-155">Your app is now registered with Azure AD, and has been assigned a client ID.</span></span> <span data-ttu-id="0c480-156">Однако осталось настроить еще несколько важных аспектов приложения.</span><span class="sxs-lookup"><span data-stu-id="0c480-156">However, there are several important aspects of your app left to configure.</span></span>
    

### <a name="configure-your-application-properties-in-azure-ad"></a><span data-ttu-id="0c480-157">Настройка свойств приложения в Azure AD</span><span class="sxs-lookup"><span data-stu-id="0c480-157">Configure your application properties in Azure AD</span></span>

<span data-ttu-id="0c480-158">Теперь, когда приложение зарегистрировано, необходимо указать несколько важных свойств, определяющих, как приложение работает в Azure AD и как администраторы клиентов разрешают приложению получать доступ к их данным с помощью API управления Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-158">Now that your application is registered, there are several important properties you must specify that determine how your application functions within Azure AD and how tenant admins will grant consent to allow your application to access their data by using the Office 365 Management APIs.</span></span>

<span data-ttu-id="0c480-159">Дополнительные сведения о настройке приложений Azure AD в целом см. в статье [Объекты приложения и субъекта-службы в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects).</span><span class="sxs-lookup"><span data-stu-id="0c480-159">For more information about Azure AD application configuration in general, see [Application Object Properties](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects).</span></span>


1. <span data-ttu-id="0c480-160">**Идентификатор клиента.**</span><span class="sxs-lookup"><span data-stu-id="0c480-160">**CLIENT ID**.</span></span> <span data-ttu-id="0c480-161">Это значение автоматически создается службой Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0c480-161">This value is automatically generated by Azure AD.</span></span> <span data-ttu-id="0c480-162">Затем приложение будет использовать это значение, запрашивая согласие у администраторов клиентов и маркеры только для приложений из службы Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0c480-162">Your application will use this value when requesting consent from tenant admins and when requesting app-only tokens from Azure AD.</span></span>
    
2. <span data-ttu-id="0c480-163">**Приложение является мультитенантным.**</span><span class="sxs-lookup"><span data-stu-id="0c480-163">**APPLICATION IS MULTI-TENANT**.</span></span> <span data-ttu-id="0c480-164">Для этого свойства необходимо задать значение **Да**, чтобы администраторы клиентов могли разрешать приложению доступ к своим данным с помощью API управления Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-164">This property must be set to **YES** to allow tenant admins to grant consent to your app to access their data by using the Office 365 Management APIs.</span></span> <span data-ttu-id="0c480-165">Если для этого свойства выбрано значение **Нет**, то приложение сможет получать доступ только к данным вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-165">If this property is set to **NO**, your application will only be able to access your own tenant's data.</span></span>
    
3. <span data-ttu-id="0c480-166">**URL-адрес ответа.**</span><span class="sxs-lookup"><span data-stu-id="0c480-166">**REPLY URL**.</span></span> <span data-ttu-id="0c480-167">Это URL-адрес, на который перенаправляется администратор клиента, после того как приложению дается согласие на доступ к данным с помощью API управления Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-167">This is the URL that a tenant admin will be redirected to after granting consent to allow your application to access their data by using the Office 365 Management APIs.</span></span> <span data-ttu-id="0c480-168">При необходимости можно задать несколько URL-адресов ответа.</span><span class="sxs-lookup"><span data-stu-id="0c480-168">You can configure multiple reply URLs as needed.</span></span> <span data-ttu-id="0c480-169">Azure автоматически задает первый в соответствии с URL-адресом для входа, указанным при создании приложения, но при необходимости это значение можно изменить.</span><span class="sxs-lookup"><span data-stu-id="0c480-169">Azure automatically sets the first one to match the sign-on URL you specified when you created the application, but you can change this value as needed.</span></span>
    
<span data-ttu-id="0c480-170">Не забывайте нажимать кнопку **Сохранить** после внесения каких-либо изменений в эти свойства.</span><span class="sxs-lookup"><span data-stu-id="0c480-170">Be sure to choose **Save** after making any changes to these properties.</span></span>


### <a name="generate-a-new-key-for-your-application"></a><span data-ttu-id="0c480-171">Создание нового ключа для приложения</span><span class="sxs-lookup"><span data-stu-id="0c480-171">Generate a new key for your application</span></span>

<span data-ttu-id="0c480-172">Ключи, также называемые секретами клиентов, используются при обмене кода авторизации на маркер доступа.</span><span class="sxs-lookup"><span data-stu-id="0c480-172">Keys, also known as client secrets, are used when exchanging an authorization code for an access token.</span></span>


1. <span data-ttu-id="0c480-173">На портале управления Azure выберите свое приложение и нажмите **Настройка** в верхнем меню.</span><span class="sxs-lookup"><span data-stu-id="0c480-173">In the Azure Management Portal, select your application and choose **Configure** in the top menu.</span></span> <span data-ttu-id="0c480-174">Прокрутите вниз до строки **ключи**.</span><span class="sxs-lookup"><span data-stu-id="0c480-174">Scroll down to **keys**.</span></span>
    
2. <span data-ttu-id="0c480-175">Выберите длительность для ключа и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="0c480-175">Select the duration for your key, and choose **Save**.</span></span>
    
   ![Страница подписки Azure](images/azure-subscription-page.png)
    
    
3. <span data-ttu-id="0c480-177">Azure показывает секрет приложения только после его сохранения.</span><span class="sxs-lookup"><span data-stu-id="0c480-177">Azure displays the app secret only after saving it.</span></span> <span data-ttu-id="0c480-178">Нажмите значок буфера обмена, чтобы скопировать секрет клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-178">Select the Clipboard icon to copy the client secret to the Clipboard.</span></span>
    
   ![Страница портала Azure](images/azure-portal-page.png)

   > [!IMPORTANT] 
   > <span data-ttu-id="0c480-180">Azure показывает секрет клиента только в момент его создания.</span><span class="sxs-lookup"><span data-stu-id="0c480-180">Azure only displays the client secret at the time you initially generate it.</span></span> <span data-ttu-id="0c480-181">Вернуться на эту страницу и получить секрет клиента позже будет невозможно.</span><span class="sxs-lookup"><span data-stu-id="0c480-181">You cannot navigate back to this page and retrieve the client secret later.</span></span>

### <a name="configure-an-x509-certificate-to-enable-service-to-service-calls"></a><span data-ttu-id="0c480-182">Настройка сертификата X.509 для поддержки вызовов между службами</span><span class="sxs-lookup"><span data-stu-id="0c480-182">Configure an X.509 certificate to enable service-to-service calls</span></span>

<span data-ttu-id="0c480-183">Приложение, работающее в фоновом режиме, например управляющая программа или служба, может использовать учетные данные клиента, чтобы запрашивать маркеры доступа только для приложений без постоянных запросов согласия от администратора клиента после предоставления первоначального согласия.</span><span class="sxs-lookup"><span data-stu-id="0c480-183">An application that is running in the background, such as a daemon or service, can use client credentials to request app-only access tokens without repeatedly requesting consent from the tenant admin after initial consent is granted.</span></span> 

<span data-ttu-id="0c480-184">Дополнительные сведения см. в статье [Вызовы между службами с использованием учетных данных клиентов](https://msdn.microsoft.com/library/azure/dn645543.aspx).</span><span class="sxs-lookup"><span data-stu-id="0c480-184">For more information, see [Service to Service Calls Using Client Credentials](https://msdn.microsoft.com/library/azure/dn645543.aspx).</span></span>

<span data-ttu-id="0c480-185">Необходимо настроить сертификат X.509 для приложения, который будет использоваться в качестве учетных данных клиента при запрашивании маркеров доступа только для приложений из Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0c480-185">You must configure an X.509 certificate with your application to be used as client credentials when requesting app-only access tokens from Azure AD.</span></span> <span data-ttu-id="0c480-186">Этот процесс состоит из двух этапов:</span><span class="sxs-lookup"><span data-stu-id="0c480-186">There are two steps to the process:</span></span>

- <span data-ttu-id="0c480-187">Получение сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="0c480-187">Obtain an X.509 certificate.</span></span> <span data-ttu-id="0c480-188">Вы можете использовать сертификат, выданный доверенным центром сертификации, или самозаверяющий сертификат.</span><span class="sxs-lookup"><span data-stu-id="0c480-188">You can use a self-signed certificate or a certificate issued by publicly trusted certificate authority.</span></span>
    
- <span data-ttu-id="0c480-189">Измените манифест приложения, включающий отпечаток и открытый ключ сертификата.</span><span class="sxs-lookup"><span data-stu-id="0c480-189">Modify your application manifest to include the thumbprint and public key of your certificate.</span></span>
    
<span data-ttu-id="0c480-190">В приведенных ниже инструкциях показано, как использовать Visual Studio или средство _makecert_ из пакета Windows SDK, чтобы создать самозаверяющий сертификат и экспортировать открытый ключ в файл с кодировкой base64.</span><span class="sxs-lookup"><span data-stu-id="0c480-190">The following instructions show you how to use the Visual Studio or Windows SDK _makecert_ tool to generate a self-signed certificate and export the public key to a base64-encoded file.</span></span>


1. <span data-ttu-id="0c480-191">В командной строке выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="0c480-191">From the command line, run the following:</span></span>
    
   ```
    makecert -r -pe -n "CN=MyCompanyName MyAppName Cert" -b 03/15/2015 -e 03/15/2017 -ss my -len 2048
   ```

   > [!NOTE] 
   > <span data-ttu-id="0c480-192">Создавая сертификат X.509, убедитесь, что длина ключа составляет как минимум 2048.</span><span class="sxs-lookup"><span data-stu-id="0c480-192">When you are generating the X.509 certificate, make sure the key length is at least 2048.</span></span> <span data-ttu-id="0c480-193">Ключи с меньшей длиной не принимаются как допустимые.</span><span class="sxs-lookup"><span data-stu-id="0c480-193">Shorter key lengths are not accepted as valid keys.</span></span>

2. <span data-ttu-id="0c480-194">Откройте оснастку MMC для сертификатов и подключитесь к своей учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="0c480-194">Open the Certificates MMC snap-in and connect to your user account.</span></span> 
    
3. <span data-ttu-id="0c480-195">Найдите новый сертификат в папке "Личные" и экспортируйте открытый ключ в файл с кодировкой base64 (например, mycompanyname.cer).</span><span class="sxs-lookup"><span data-stu-id="0c480-195">Find the new certificate in the Personal folder and export the public key to a base64-encoded file (for example, mycompanyname.cer).</span></span> <span data-ttu-id="0c480-196">Приложение будет использовать этот сертификат для связи с Azure AD, поэтому необходимо также сохранить доступ к открытому ключу.</span><span class="sxs-lookup"><span data-stu-id="0c480-196">Your application will use this certificate to communicate with Azure AD, so make sure you retain access to the private key as well.</span></span>
    
   > [!NOTE] 
   > <span data-ttu-id="0c480-197">Вы можете использовать Windows PowerShell, чтобы извлечь отпечаток и открытый ключ с кодировкой base64.</span><span class="sxs-lookup"><span data-stu-id="0c480-197">You can use Windows PowerShell to extract the thumbprint and base64-encoded public key.</span></span> <span data-ttu-id="0c480-198">Другие платформы предоставляют подобные средства для получения свойств сертификатов.</span><span class="sxs-lookup"><span data-stu-id="0c480-198">Other platforms provide similar tools to retrieve properties of certificates.</span></span>

4. <span data-ttu-id="0c480-199">В командной строке Windows PowerShell введите и выполните указанные команды.</span><span class="sxs-lookup"><span data-stu-id="0c480-199">From the Windows PowerShell prompt, type and run the following:</span></span>
    
   ```powershell
    $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
    $cer.Import("mycer.cer")
    $bin = $cer.GetRawCertData()
    $base64Value = [System.Convert]::ToBase64String($bin)
    $bin = $cer.GetCertHash()
    $base64Thumbprint = [System.Convert]::ToBase64String($bin)
    $keyid = [System.Guid]::NewGuid().ToString()
   ```

5. <span data-ttu-id="0c480-200">Сохраните значения `$base64Thumbprint`, `$base64Value` и `$keyid` для использования при обновлении манифеста приложения на последующих этапах.</span><span class="sxs-lookup"><span data-stu-id="0c480-200">Store the values for `$base64Thumbprint`, `$base64Value`, and `$keyid` to be used when you update your application manifest in the next set of steps.</span></span>
    
   <span data-ttu-id="0c480-201">Теперь необходимо обновить манифест приложения в Azure AD, используя извлеченные из сертификата значения и созданный идентификатор ключа.</span><span class="sxs-lookup"><span data-stu-id="0c480-201">Using the values extracted from the certificate and the generated key ID, you must now update your application manifest in Azure AD.</span></span>
    
6. <span data-ttu-id="0c480-202">На портале управления Azure выберите свое приложение и нажмите **Настройка** в верхнем меню.</span><span class="sxs-lookup"><span data-stu-id="0c480-202">In the Azure Management Portal, select your application and choose **Configure** in the top menu.</span></span>
    
7. <span data-ttu-id="0c480-203">На панели команд нажмите **Управление манифестом** и выберите команду **Скачать манифест**.</span><span class="sxs-lookup"><span data-stu-id="0c480-203">In the command bar, choose **Manage manifest**, and then choose **Download Manifest**.</span></span>
    
   ![Экран сертификата командной строки](images/command-line-certificate-display.png)
    
    
8. <span data-ttu-id="0c480-205">Откройте загруженный манифест для редактирования и замените пустое свойство KeyCredentials на следующий код JSON:</span><span class="sxs-lookup"><span data-stu-id="0c480-205">Open the downloaded manifest for editing and replace the empty KeyCredentials property with the following JSON:</span></span>
    
   ```json
      "keyCredentials": [
        {
            "customKeyIdentifier" : "$base64Thumbprint_from_above",
            "keyId": "$keyid_from_above",
            "type": "AsymmetricX509Cert",
            "usage": "Verify",
            "value": "$base64Value_from_above"
        }
    ],
   ```


   > [!NOTE] 
   > <span data-ttu-id="0c480-206">Свойство [KeyCredentials](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType) представляет собой коллекцию, что позволяет отправлять несколько сертификатов X.509 для сценариев переключения или удалять сертификаты с целью компромисса.</span><span class="sxs-lookup"><span data-stu-id="0c480-206">The [KeyCredentials](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType) property is a collection, making it possible to upload multiple X.509 certificates for rollover scenarios or delete certificates for compromise scenarios.</span></span>

9. <span data-ttu-id="0c480-207">Сохраните изменения и отправьте обновленный манифест, выбрав элемент **Управление манифестом** на панели команд, нажав **Отправить манифест** и выбрав обновленный файл манифеста.</span><span class="sxs-lookup"><span data-stu-id="0c480-207">Save your changes and upload the updated manifest by choosing **Manage manifest** in the command bar, choosing **Upload manifest**, browsing to your updated manifest file, and then selecting it.</span></span>
    

### <a name="specify-the-permissions-your-app-requires-to-access-the-office-365-management-apis"></a><span data-ttu-id="0c480-208">Указание разрешений, необходимых приложению для доступа к API управления Office 365</span><span class="sxs-lookup"><span data-stu-id="0c480-208">Specify the permissions your app requires to access the Office 365 Management APIs</span></span>

<span data-ttu-id="0c480-209">Наконец, вам нужно точно указать, какие разрешения требует ваше приложение от API управления Office 365.</span><span class="sxs-lookup"><span data-stu-id="0c480-209">Finally, you need to specify exactly what permissions your app requires of the Office 365 Management APIs.</span></span> <span data-ttu-id="0c480-210">Для этого следует предоставить приложению доступ к API управления Office 365, а затем задать нужные разрешения.</span><span class="sxs-lookup"><span data-stu-id="0c480-210">To do so, you add access to the Office 365 Management APIs to your app, and then you specify the permission(s) you need.</span></span>


1. <span data-ttu-id="0c480-211">На портале управления Azure выберите свое приложение и нажмите **Настройка** в верхнем меню.</span><span class="sxs-lookup"><span data-stu-id="0c480-211">In the Azure Management Portal, select your application, and choose **Configure** in the top menu.</span></span> <span data-ttu-id="0c480-212">Прокрутите вниз до раздела **Разрешения для других приложений** и нажмите **Добавить приложение**.</span><span class="sxs-lookup"><span data-stu-id="0c480-212">Scroll down to **permissions to other applications**, and choose **Add application**.</span></span>
    
   ![Страница Azure AD](images/azure-ad-page.png)
    
    
2. <span data-ttu-id="0c480-214">Выберите **API управления Office 365** (1), чтобы этот пункт появился в столбце **Выбрано** (2), а затем установите флажок в правом нижней углу (3), чтобы сохранить выбор, и вернитесь на главную страницу конфигурации для приложения.</span><span class="sxs-lookup"><span data-stu-id="0c480-214">Select the **Office 365 Management APIs** (1) so that it appears in the **Selected** column (2), and then select the check mark in the lower right (3) to save your selection and return to the main configuration page for your application.</span></span>
    
   ![Страница приложений Azure AD](images/azure-ad-apps-page.png)
    
    
3. <span data-ttu-id="0c480-216">Теперь API управления Office отображаются в списке приложений, для которого приложению требуются разрешения.</span><span class="sxs-lookup"><span data-stu-id="0c480-216">The Office Management APIs now appear in the list of applications to which your application requires permissions.</span></span> <span data-ttu-id="0c480-217">В разделах **Разрешения приложения** и **Делегированные разрешения** выберите разрешения, необходимые приложению.</span><span class="sxs-lookup"><span data-stu-id="0c480-217">Under both **Application Permissions** and **Delegated Permissions**, select the permissions your application requires.</span></span> <span data-ttu-id="0c480-218">Дополнительные сведения о каждом разрешении представлены в справочнике по определенному API.</span><span class="sxs-lookup"><span data-stu-id="0c480-218">Refer to the specific API reference for more details about each permission.</span></span>  

   > [!NOTE] 
   > <span data-ttu-id="0c480-219">В настоящее время существует четыре неиспользуемых разрешения, связанных с отчетами об активности и аналитикой угроз, которые будут удалены в будущем.</span><span class="sxs-lookup"><span data-stu-id="0c480-219">There are currently four unused permissions related to activity reports and threat intelligence that will be removed in the future.</span></span> <span data-ttu-id="0c480-220">Не выбирайте никакие из этих разрешений, так как в них нет необходимости.</span><span class="sxs-lookup"><span data-stu-id="0c480-220">Do not select any of these permissions because they are unnecessary.</span></span>
    
   ![Диалоговое окно добавления приложения](images/add-an-application-dialog.png)
    
    
4. <span data-ttu-id="0c480-222">Нажмите кнопку **Сохранить**, чтобы сохранить конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="0c480-222">Choose **Save** to save the configuration.</span></span>
    

## <a name="get-office-365-tenant-admin-consent"></a><span data-ttu-id="0c480-223">Получение согласия администратора клиента Office 365</span><span class="sxs-lookup"><span data-stu-id="0c480-223">Get Office 365 tenant admin consent</span></span>

<span data-ttu-id="0c480-224">Теперь, когда для приложения настроены разрешения, необходимые для использования API управления Office 365, администратор клиента должен явно предоставить приложению эти разрешения, чтобы получать доступ к данным клиента с помощью интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="0c480-224">Now that your application is configured with the permissions it needs to use the Office 365 Management APIs, a tenant admin must explicitly grant your application these permissions in order to access their tenant's data by using the APIs.</span></span> <span data-ttu-id="0c480-225">Чтобы дать согласие, администратор клиента должен войти в Azure AD, используя указанный ниже специальный URL-адрес, и просмотреть запрашиваемые приложением разрешения.</span><span class="sxs-lookup"><span data-stu-id="0c480-225">To grant consent, the tenant admin must sign in to Azure AD by using the following specially constructed URL, where they can review your application's requested permissions.</span></span> <span data-ttu-id="0c480-226">Это действие не требуется при использовании API для доступа к данным из собственного клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-226">This step is not required when using the APIs to access data from your own tenant.</span></span>


```http
https://login.windows.net/common/oauth2/authorize?response_type=code&resource=https%3A%2F%2Fmanage.office.com&client_id={your_client_id}&redirect_uri={your_redirect_url }
```

<span data-ttu-id="0c480-227">URL-адрес перенаправления должен совпадать с одним из URL-адресов, заданных для приложения в Azure AD, или быть его дочерним путем.</span><span class="sxs-lookup"><span data-stu-id="0c480-227">The redirect URL must match or be a sub-path under one of the Reply URLs configured for your application in Azure AD.</span></span>

<span data-ttu-id="0c480-228">Пример:</span><span class="sxs-lookup"><span data-stu-id="0c480-228">For example:</span></span>

```http
https://login.windows.net/common/oauth2/authorize?response_type=code&resource=https%3A%2F%2Fmanage.office.com&client_id=2d4d11a2-f814-46a7-890a-274a72a7309e&redirect_uri=http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F
```

<span data-ttu-id="0c480-229">Вы можете тестировать URL-адрес согласия, вставив его в браузере и выполнив вход с использованием учетных данных администратора Office 365 для того клиента, который использовался при регистрации приложения.</span><span class="sxs-lookup"><span data-stu-id="0c480-229">You can test the consent URL by pasting it into a browser and signing in using the credentials of an Office 365 admin for a tenant other than the tenant that you used to register the application.</span></span> <span data-ttu-id="0c480-230">Вы увидите запрос на предоставление приложению разрешения на использование API управления Office.</span><span class="sxs-lookup"><span data-stu-id="0c480-230">You will see the request to grant your application permission to use the Office Management APIs.</span></span>


![Страница добавленного приложения в Azure AD](images/azure-ad-app-added-page.png)

<span data-ttu-id="0c480-232">Нажав кнопку **Принять**, вы перейдете на указанную страницу, а в строке запроса будет указан код.</span><span class="sxs-lookup"><span data-stu-id="0c480-232">After choosing **Accept**, you are redirected to the specified page, and there will be a code in the query string.</span></span> 

<span data-ttu-id="0c480-233">Пример:</span><span class="sxs-lookup"><span data-stu-id="0c480-233">For example:</span></span>

```http
http://www.mycompany.com/myapp/?code=AAABAAAAvPM1KaPlrEqdFSB...
```

<span data-ttu-id="0c480-234">Приложение использует этот код авторизации, чтобы получить из Azure AD маркер доступа, из которого затем можно извлечь идентификатор клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-234">Your application uses this authorization code to obtain an access token from Azure AD, from which the tenant ID can be extracted.</span></span> <span data-ttu-id="0c480-235">Когда вы получите и сохраните идентификатор клиента, администратору клиента больше не потребуется входить для получения последующих маркеров доступа.</span><span class="sxs-lookup"><span data-stu-id="0c480-235">After you have extracted and stored the tenant ID, you can obtain subsequent access tokens without requiring the tenant admin to sign in.</span></span>


## <a name="request-access-tokens-from-azure-ad"></a><span data-ttu-id="0c480-236">Запросы маркеров доступа из Azure AD</span><span class="sxs-lookup"><span data-stu-id="0c480-236">Request access tokens from Azure AD</span></span>

<span data-ttu-id="0c480-237">Запрашивать маркеры доступа из Azure AD можно двумя способами:</span><span class="sxs-lookup"><span data-stu-id="0c480-237">There are two methods for requesting access tokens from Azure AD:</span></span>

- <span data-ttu-id="0c480-238">[Поток предоставления кода авторизации](https://msdn.microsoft.com/library/azure/dn645542.aspx) включает предоставление явного согласия администратором клиента, в результате чего приложению возвращается код авторизации.</span><span class="sxs-lookup"><span data-stu-id="0c480-238">The [Authorization Code Grant Flow](https://msdn.microsoft.com/library/azure/dn645542.aspx) involves a tenant admin granting explicit consent, which returns an authorization code to your application.</span></span> <span data-ttu-id="0c480-239">Затем приложение обменивает код авторизации на маркер доступа.</span><span class="sxs-lookup"><span data-stu-id="0c480-239">Your application then exchanges the authorization code for an access token.</span></span> <span data-ttu-id="0c480-240">Этот способ необходим, чтобы получить первоначальное согласие, нужное приложению для доступа к данным клиента с помощью API, а этот первый маркер доступа необходим для получения и хранения идентификатора клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-240">This method is required to obtain the initial consent that your application needs to access the tenant data by using the API, and this first access token is needed in order to obtain and store the tenant ID.</span></span>
    
- <span data-ttu-id="0c480-241">[Поток предоставления учетных данных клиента](https://msdn.microsoft.com/library/azure/dn645543.aspx) позволяет приложению запрашивать последующие маркеры доступа по мере устаревания предыдущих. При этом администратору клиента не требуется выполнять вход и явно предоставлять согласие.</span><span class="sxs-lookup"><span data-stu-id="0c480-241">The [Client Credentials Grant Flow](https://msdn.microsoft.com/library/azure/dn645543.aspx) allows your application to request subsequent access tokens as old ones expire, without requiring the tenant admin to sign in and explicitly grant consent.</span></span> <span data-ttu-id="0c480-242">Этот способ необходимо использовать для приложений, непрерывно работающих в фоновом режиме, вызывая API после предоставления первоначального согласия администратором клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-242">This method must be used for applications that run continuously in the background calling the APIs once the initial tenant admin consent has been granted.</span></span>
    

### <a name="request-an-access-token-using-the-authorization-code"></a><span data-ttu-id="0c480-243">Запрос маркера доступа с помощью кода авторизации</span><span class="sxs-lookup"><span data-stu-id="0c480-243">Request an access token using the authorization code</span></span>

<span data-ttu-id="0c480-244">Когда администратор клиента дает согласие, приложение получает код авторизации в качестве параметра строки запроса, когда Azure AD перенаправляет администратора клиента по специальному URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="0c480-244">After a tenant admin grants consent, your application receives an authorization code as a query string parameter when Azure AD redirects the tenant admin to your designated URL.</span></span>

```http
http://www.mycompany.com/myapp/?code=AAABAAAAvPM1KaPlrEqdFSB...
```

<span data-ttu-id="0c480-245">Приложение отправляет HTTP-запрос REST POST в Azure AD, чтобы обменять код авторизации на маркер доступа.</span><span class="sxs-lookup"><span data-stu-id="0c480-245">Your application makes an HTTP REST POST to Azure AD to exchange the authorization code for an access token.</span></span> <span data-ttu-id="0c480-246">Так как идентификатор клиента пока не известен, запрос POST будет адресован "общей" конечной точке, идентификатор клиента для которой не включен в URL-адрес:</span><span class="sxs-lookup"><span data-stu-id="0c480-246">Because the tenant ID is not yet known, the POST will be to the "common" endpoint, which does not have the tenant ID embedded in the URL:</span></span>

```http
https://login.windows.net/common/oauth2/token
```

<span data-ttu-id="0c480-247">Текст запроса POST содержит следующие данные:</span><span class="sxs-lookup"><span data-stu-id="0c480-247">The body of the POST contains the following:</span></span>

```json
resource=https%3A%2F%2Fmanage.office.com&amp;client_id=a6099727-6b7b-482c-b509-1df309acc563 &amp;redirect_uri= http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F &amp;client_secret={your_client_key}&amp;grant_type=authorization_code&amp;code= AAABAAAAvPM1KaPlrEqdFSB...
```

#### <a name="sample-request"></a><span data-ttu-id="0c480-248">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="0c480-248">Sample request</span></span>

```json
POST https://login.windows.net/common/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.windows.net
Content-Length: 944

resource=https%3A%2F%2Fmanage.office.com&amp;client_id=a6099727-6b7b-482c-b509-1df309acc563 &amp;redirect_uri= http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F &amp;client_secret={your_client_key}&amp;grant_type=authorization_code&amp;code=AAABAAAAvPM1KaPlrEqdFSB...
```

<br/>

<span data-ttu-id="0c480-249">Текст отклика будет включать ряд свойств, в том числе маркер доступа.</span><span class="sxs-lookup"><span data-stu-id="0c480-249">The body of the response will include several properties, including the access token.</span></span> 

#### <a name="sample-response"></a><span data-ttu-id="0c480-250">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="0c480-250">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Content-Length: 3265

{"expires_in":"3599","token_type":"Bearer","scope":"ActivityFeed.Read ActivityReports.Read ServiceHealth.Read","expires_on":"1438290275","not_before":"1438286375","resource":"https://manage.office.com","access_token":"eyJ0eX...","refresh_token":"AAABAAA...","id_token":"eyJ0eXAi..."}
```

<span data-ttu-id="0c480-251">Возвращаемый маркер доступа представляет собой токен JWT, содержащий сведения об администраторе, давшем согласие, и приложении, запрашивающем доступ.</span><span class="sxs-lookup"><span data-stu-id="0c480-251">The access token that is returned is a JWT token that includes information about both the admin that granted consent and the application requesting access.</span></span> <span data-ttu-id="0c480-252">Ниже показан пример незакодированного маркера.</span><span class="sxs-lookup"><span data-stu-id="0c480-252">The following shows an example of an un-encoded token.</span></span> <span data-ttu-id="0c480-253">Приложение должно извлечь из этого токена идентификатор клиента tid и сохранить его, чтобы можно было запрашивать дополнительные маркеры доступа по окончании срока действия старых без дальнейшего участия администратора.</span><span class="sxs-lookup"><span data-stu-id="0c480-253">Your application must extract the tenant ID "tid" from this token and store it so that it can be used to request additional access tokens as they expire, without further admin interaction.</span></span>

#### <a name="sample-token"></a><span data-ttu-id="0c480-254">Пример маркера</span><span class="sxs-lookup"><span data-stu-id="0c480-254">Sample token</span></span>

```json
{
  "aud": "https://manage.office.com",
  "iss": "https://sts.windows.net/41463f53-8812-40f4-890f-865bf6e35190/",
  "iat": 1427246416,
  "nbf": 1427246416,
  "exp": 1427250316,
  "ver": "1.0",
  "tid": "41463f53-8812-40f4-890f-865bf6e35190",
  "amr": [
    "pwd"
  ],
  "oid": "1cef1fdb-ff52-48c4-8e4e-dfb5ea83d357",
  "upn": "admin@contoso.onmicrosoft.com",
  "puid": "1003BFFD8EC47CA6",
  "sub": "7XpD5OWAXM1OWmKiVKh1FOkKXV4N3OSRol6mz1pxxhU",
  "given_name": "John",
  "family_name": "Doe",
  "name": "Contoso, Inc.",
  "unique_name": "admin@contoso.onmicrosoft.com",
  "appid": "a6099727-6b7b-482c-b509-1df309acc563",
  "appidacr": "1",
  "scp": "ActivityFeed.Read ServiceHealth.Read",
  "acr": "1"
}
```

### <a name="request-an-access-token-by-using-client-credentials"></a><span data-ttu-id="0c480-255">Запрос маркера доступа с помощью учетных данных клиента</span><span class="sxs-lookup"><span data-stu-id="0c480-255">Request an access token by using client credentials</span></span>

<span data-ttu-id="0c480-256">Узнав идентификатор клиента, приложение может совершать вызовы Azure AD между службами, чтобы запрашивать дополнительные маркеры доступа по мере их устаревания.</span><span class="sxs-lookup"><span data-stu-id="0c480-256">After the tenant ID is known, your application can make service-to-service calls to Azure AD to request additional access tokens as they expire.</span></span> <span data-ttu-id="0c480-257">Эти маркеры содержат сведения только о запрашивающем приложении. В них нет данных об администраторе, который изначально дал согласие.</span><span class="sxs-lookup"><span data-stu-id="0c480-257">These tokens include information only about the requesting application and not about the admin that originally granted consent.</span></span> <span data-ttu-id="0c480-258">Для вызовов между службами требуется, чтобы приложение использовало сертификат X.509 для создания клиентского утверждения в виде токена носителя JWT с кодировкой base64 и подписью SHA256.</span><span class="sxs-lookup"><span data-stu-id="0c480-258">Service-to-service calls require that your application use an X.509 certificate to create client assertion in the form of a base64-encoded, SHA256 signed JWT bearer token.</span></span>

<span data-ttu-id="0c480-259">Во время разработки приложения на платформе .NET можно создавать клиентские утверждения с помощью [библиотеки проверки подлинности Azure AD (ADAL)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries).</span><span class="sxs-lookup"><span data-stu-id="0c480-259">When you are developing your application in .NET, you can use the [Azure AD Authentication Library (ADAL)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) to create client assertions.</span></span> <span data-ttu-id="0c480-260">На других платформах разработки должны быть доступны похожие библиотеки.</span><span class="sxs-lookup"><span data-stu-id="0c480-260">Other development platforms should have similar libraries.</span></span>

<span data-ttu-id="0c480-261">Незакодированный токен JWT состоит из заголовка и полезных данных с указанными ниже свойствами.</span><span class="sxs-lookup"><span data-stu-id="0c480-261">An un-encoded JWT token consists of a header and payload that have the following properties.</span></span>

```json
HEADER:

{
  "alg": "RS256",
  "x5t": "{thumbprint of your X.509 certificate used to sign the token",
}

PAYLOAD:

{
  "aud": "https://login.windows.net/{tenantid}/oauth2/token",
  "iss": "{your app client ID}",
  "sub": "{your app client ID}"
  "jti": "{random GUID}",
  "nbf": {epoch time, before which the token is not valid},
  "exp": {epoch time, after which the token is not valid},
}

```

#### <a name="sample-jwt-token"></a><span data-ttu-id="0c480-262">Пример токена JWT</span><span class="sxs-lookup"><span data-stu-id="0c480-262">Sample JWT token</span></span>


```json
HEADER:

{
  "alg": "RS256",
  "x5t": "YyfshJC3rPQ-kpGo5dUaiY5t3iU",
}

PAYLOAD:

{
  "aud": "https://login.windows.net/41463f53-8812-40f4-890f-865bf6e35190/oauth2/token",
  "iss": "a6099727-6b7b-482c-b509-1df309acc563",
  "sub": "a6099727-6b7b-482c-b509-1df309acc563"
  "jti": "0ce254c4-81b1-4a2e-8436-9a8c3b49dfb9",
  "nbf": 1427248048,
  "exp": 1427248648,
}
```

<span data-ttu-id="0c480-263">Затем клиентское утверждение передается в Azure AD в составе вызова между службами, чтобы запросить маркер доступа.</span><span class="sxs-lookup"><span data-stu-id="0c480-263">The client assertion is then passed to Azure AD as part of a service-to-service call to request an access token.</span></span> <span data-ttu-id="0c480-264">Запрашивая маркер доступа с помощью учетных данных клиента, используйте запрос HTTP POST к конечной точке определенного клиента, где ранее извлеченный и сохраненный идентификатор клиента внедряется в URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="0c480-264">When using client credentials to request an access token, use an HTTP POST to a tenant-specific endpoint, where the previously extracted and stored tenant ID is embedded in the URL.</span></span>


```http
https://login.windows.net/{tenantid}/oauth2/token
```

<span data-ttu-id="0c480-265">Текст запроса POST содержит следующие данные:</span><span class="sxs-lookup"><span data-stu-id="0c480-265">The body of the POST contains the following:</span></span>


```json
resource=https%3A%2F%2Fmanage.office.com&amp;client_id={your_app_client_id}&amp;grant_type=client_credentials&amp;client_assertion_type=urn%3Aietf%3Aparams%3Aoauth%3Aclient-assertion-type%3Ajwt-bearer&amp;client_assertion={encoded_signed_JWT_token}
```

#### <a name="sample-request"></a><span data-ttu-id="0c480-266">Пример запроса</span><span class="sxs-lookup"><span data-stu-id="0c480-266">Sample request</span></span>

```json
POST https://login.windows.net/41463f53-8812-40f4-890f-865bf6e35190/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.windows.net
Content-Length: 994

resource=https%3A%2F%2Fmanage.office.com&amp;client_id= a6099727-6b7b-482c-b509-1df309acc563&amp;grant_type=client_credentials &amp;client_assertion_type=urn%3Aietf%3Aparams%3Aoauth%3Aclient-assertion-type%3Ajwt-bearer&amp;client_assertion=eyJhbGciOiJSUzI1NiIsIng1dCI6Ill5ZnNoSkMzclBRLWtwR281ZFVhaVk1dDNpVSJ9.eyJhdWQiOiJodHRwczpcL1wvbG9naW4ud2luZG93cy5uZXRcLzQxNDYzZjUzLTg4MTItNDBmNC04OTBmLTg2NWJmNmUzNTE5MFwvb2F1dGgyXC90b2tlbiIsImV4cCI6MTQyNzI0ODY0OCwiaXNzIjoiYTYwOTk3MjctNmI3Yi00ODJjLWI1MDktMWRmMzA5YWNjNTYzIiwianRpIjoiMGNlMjU0YzQtODFiMS00YTJlLTg0MzYtOWE4YzNiNDlkZmI5IiwibmJmIjoxNDI3MjQ4MDQ4LCJzdWIiOiJhNjA5OTcyNy02YjdiLTQ4MmMtYjUwOS0xZGYzMDlhY2M1NjMifQ.vfDrmCjiXgoj2JrTkwyOpr-NOeQTzlXQcGlKGNpLLe0oh4Zvjdcim5C7E0UbI3Z2yb9uKQdx9G7GeqS-gVc9kNV_XSSNP4wEQj3iYNKpf_JD2ikUVIWBkOg41BiTuknRJAYOMjiuBE2a6Wyk-vPCs_JMd7Sr-N3LiNZ-TjluuVzWHfok_HWz_wH8AzdoMF3S0HtrjNd9Ld5eI7MVMt4OTpRfh-Syofi7Ow0HN07nKT5FYeC_ThBpGiIoODnMQQtDA2tM7D3D6OlLQRgLfI8ir73PVXWL7V7Zj2RcOiooIeXx38dvuSwYreJYtdphmrDBZ2ehqtduzUZhaHL1iDvLlw
```

<span data-ttu-id="0c480-267">Отклик будет таким же, как раньше, но свойства токена будут другими, так он не содержит свойства администратора, давшего согласие.</span><span class="sxs-lookup"><span data-stu-id="0c480-267">The response will be the same as before, but the token will not have the same properties, because it does not contain properties of the admin that granted consent.</span></span> 

#### <a name="sample-response"></a><span data-ttu-id="0c480-268">Пример отклика</span><span class="sxs-lookup"><span data-stu-id="0c480-268">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Content-Length: 1276

{"token_type":"Bearer","expires_in":"3599","expires_on":"1431659094","not_before":"1431655194","resource":"https://manage.office.com","access_token":"eyJ0eXAiOiJKV1QiL..."}
```

#### <a name="sample-access-token"></a><span data-ttu-id="0c480-269">Пример маркера доступа</span><span class="sxs-lookup"><span data-stu-id="0c480-269">Sample access token</span></span>

```json
{
  "aud": "https://manage.office.com",
  "iss": "https://sts.windows.net/41463f53-8812-40f4-890f-865bf6e35190/",
  "iat": 1431655194,
  "nbf": 1431655194,
  "exp": 1431659094,
  "ver": "1.0",
  "tid": "41463f53-8812-40f4-890f-865bf6e35190",
  "roles": [
    "ServiceHealth.Read",
    "ActivityFeed.Read"
  ],
  "oid": "67cb0334-e242-4783-8028-0f39132fb5ad",
  "sub": "67cb0334-e242-4783-8028-0f39132fb5ad",
  "idp": "https://sts.windows.net/41463f53-8812-40f4-890f-865bf6e35190/",
  "appid": "a6099727-6b7b-482c-b509-1df309acc563",
  "appidacr": "1"
}
```


## <a name="build-your-app"></a><span data-ttu-id="0c480-270">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="0c480-270">Build your app</span></span>

<span data-ttu-id="0c480-271">Теперь, когда вы зарегистрировали приложение в Azure AD и настроили для него необходимые разрешения, все готово к созданию приложения.</span><span class="sxs-lookup"><span data-stu-id="0c480-271">Now that you have registered your app in Azure AD and configured it with the necessary permissions, you're ready to build your app.</span></span> <span data-ttu-id="0c480-272">Ниже указаны некоторые ключевые аспекты, которые следует учитывать при проектировании и создании приложения.</span><span class="sxs-lookup"><span data-stu-id="0c480-272">The following are some of the key aspects to consider when designing and building your app:</span></span>

- <span data-ttu-id="0c480-273">**Предоставление согласия.**</span><span class="sxs-lookup"><span data-stu-id="0c480-273">**The consent experience**.</span></span> <span data-ttu-id="0c480-274">Чтобы получить согласие от клиента, необходимо направить его в браузере на веб-сайт Azure AD, используя описанный ранее специальный URL-адрес. Вам необходим веб-сайт, на который Azure AD перенаправит администратора после предоставления согласия.</span><span class="sxs-lookup"><span data-stu-id="0c480-274">To obtain consent from your customers, you must direct them in a browser to the Azure AD website, using the specially constructed URL described previously, and you must have a website to which Azure AD will redirect the admin once they grant consent.</span></span> <span data-ttu-id="0c480-275">Этот сайт должен извлекать код авторизации из URL-адреса и запрашивать с его помощью маркер доступа, из которого можно получить идентификатор клиента.</span><span class="sxs-lookup"><span data-stu-id="0c480-275">This website must extract the authorization code from the URL and use it to request an access token from which it can obtain the tenant ID.</span></span>
    
- <span data-ttu-id="0c480-276">**Сохранение идентификатора клиента в системе.**</span><span class="sxs-lookup"><span data-stu-id="0c480-276">**Store the tenant ID in your system**.</span></span> <span data-ttu-id="0c480-277">Это потребуется при запрашивании маркеров доступа из Azure AD и вызове API управления Office.</span><span class="sxs-lookup"><span data-stu-id="0c480-277">This will be needed when requesting access tokens from Azure AD and when calling the Office Management APIs.</span></span>
    
- <span data-ttu-id="0c480-278">**Управление маркерами доступа.**</span><span class="sxs-lookup"><span data-stu-id="0c480-278">**Managing access tokens**.</span></span> <span data-ttu-id="0c480-279">Вам потребуется компонент, который запрашивает и контролирует маркеры доступа по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="0c480-279">You will need a component that requests and manages access tokens as needed.</span></span> <span data-ttu-id="0c480-280">Если приложение периодически вызывает интерфейсы API, оно может получать маркеры по требованию, а если оно непрерывно вызывает API для получения данных, можно запрашивать маркеры с определенным интервалом (например, каждые 45 минут).</span><span class="sxs-lookup"><span data-stu-id="0c480-280">If your app calls the APIs periodically, it can request tokens on demand, or if it calls the APIs continuously to retrieve data, it can request tokens at regular intervals (for example, every 45 minutes).</span></span>
    
- <span data-ttu-id="0c480-281">**Реализуйте прослушиватель веб-перехватчика** в соответствии с потребностями используемого API.</span><span class="sxs-lookup"><span data-stu-id="0c480-281">**Implement a webhook listener** as needed by the particular API you are using.</span></span>
    
- <span data-ttu-id="0c480-282">**Извлечение и хранение данных.**</span><span class="sxs-lookup"><span data-stu-id="0c480-282">**Data retrieval and storage**.</span></span> <span data-ttu-id="0c480-283">Вам потребуется компонент, который получает данные для каждого клиента либо путем постоянного опроса, либо в ответ на уведомления веб-перехватчиков в зависимости от конкретного API.</span><span class="sxs-lookup"><span data-stu-id="0c480-283">You'll need a component that retrieves data for each tenant, either by using continuous polling or in response to webhook notifications, depending on the particular API you are using.</span></span>
    
