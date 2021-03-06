---
title: Публикация надстроек области задач и контентных надстроек в каталоге SharePoint
description: ''
ms.date: 01/23/2018
---

# <a name="publish-task-pane-and-content-add-ins-to-a-sharepoint-catalog"></a>Публикация надстроек области задач и контентных надстроек в каталоге SharePoint

Каталог надстроек — это отдельное семейство веб-сайтов в веб-приложении SharePoint или клиенте SharePoint Online, в котором размещены библиотеки документов для надстроек Office и SharePoint. Администраторы могут отправлять в него файлы манифестов надстроек Office, чтобы пользователи в организации могли получить доступ к этим надстройкам. Когда администратор зарегистрирует каталог надстроек как доверенный, пользователи смогут вставлять надстройки в клиентском приложении Office.

> [!IMPORTANT]
> - Каталоги надстроек в SharePoint не поддерживают функции надстроек, реализованные в узле `VersionOverrides` [манифеста надстройки](../develop/add-in-manifests.md), такие как команды надстроек.
> - Чтобы публиковать надстройки для облачной или гибридной среды, рекомендуем использовать [централизованное развертывание через Центр администрирования Office 365](../publish/centralized-deployment.md).
> - Каталоги SharePoint не поддерживаются в Office 2016 для Mac. Для развертывания надстроек Office на клиентах Mac нужно отправить их в [AppSource](https://docs.microsoft.com/ru-ru/office/dev/store/submit-to-the-office-store).   

## <a name="set-up-an-add-in-catalog"></a>Настройка каталога надстроек

Выполните действия, описанные в одном из указанных ниже разделов, чтобы настроить каталог надстроек в SharePoint или Office 365.

### <a name="to-set-up-an-add-in-catalog-on-sharepoint"></a>Настройка каталога надстроек в SharePoint

1. Откройте **сайт центра администрирования** (**Пуск** > **Все программы** > **Продукты Microsoft SharePoint 2013** > **Центр администрирования SharePoint 2013**).
    
2. В области задач слева выберите пункт  **Надстройки**.
    
3. На странице  **Надстройки**, в разделе  **Управление надстройками**, выберите пункт  **Управление каталогом надстроек**.
    
4. На странице  **Управление каталогом надстроек** убедитесь, что в пункте **Селектор веб-приложения** выбрано правильное веб-приложение.
    
5. Выберите элемент  **Просмотреть параметры сайта**.
    
6. На странице  **Параметры сайта** выберите пункт **Администраторы семейства веб-сайтов**, чтобы указать администраторов семейства веб-сайтов, а затем нажмите кнопку  **ОК**.
    
7. Чтобы предоставить пользователям разрешения для сайтов, последовательно выберите элементы  **Разрешения для сайта** и **Предоставить разрешения**.
    
8. В диалоговом окне  **Общий доступ к сайту каталога приложений** укажите одного или нескольких пользователей сайта, задайте соответствующие разрешения для них, при необходимости укажите другие параметры, а затем выберите элемент **Общий доступ**.
    
9. Чтобы добавить надстройку в каталог надстроек Office, выберите **Надстройки Office**.

### <a name="to-set-up-an-add-in-catalog-on-office-365"></a>Настройка каталога надстроек в Office 365

1. На странице Центра администрирования Office 365 выберите элемент **Администратор**, а затем **SharePoint**.
    
2. В области задач слева выберите пункт  **надстройки**.
    
3. На странице  **надстройки** выберите пункт **Каталог надстроек**.
    
4. На странице  **Сайт каталога надстроек** нажмите кнопку **ОК**, чтобы принять параметр по умолчанию и создать сайт каталога надстроек.
    
5. На странице  **Создание семейства веб-сайтов каталога надстроек** укажите название сайта каталога надстроек.
    
6. Укажите адрес веб-сайта.
    
7. Минимальное допустимое значение (в данный момент оно составляет 110) указано в параметре  **Дисковая квота**. В этом семействе веб-сайтов будут устанавливаться только пакеты надстройка, которые имеют небольшой размер.
    
8. Задайте для параметра  **Квота ресурсов сервера** значение 0 (ноль). (Квота ресурсов сервера связана с регулированием изолированных решений с низкой производительностью, но на сайте каталога надстроек не будут устанавливаться изолированные решения.)
    
9. Нажмите кнопку **ОК**.
    
10. Чтобы добавить надстройку на сайт каталога надстроек, перейдите на только что созданный сайт. В области навигации слева выберите пункт **Надстройки для Office**, а затем выберите команду **новая надстройка**, чтобы отправить надстройку для файла манифеста Office.

## <a name="publish-an-add-in-to-an-add-in-catalog"></a>Публикация надстройки в каталоге надстроек

Чтобы опубликовать надстройку в каталоге надстроек, выполните указанные ниже действия.

1. Перейдите в каталог надстроек.

    - Откройте главную страницу центра администрирования SharePoint.
    
    - Выберите **Надстройки**.
    
    - Выберите **Управление каталогом надстроек**.
    
    - Выберите указанную ссылку, а затем нажмите **Надстройки Office** на левой панели навигации.
    
2. Выберите ссылку **Щелкните для добавления нового элемента**.
    
3. Нажмите кнопку **Обзор**, а затем укажите [манифест](../develop/add-in-manifests.md) для отправки.
    
    Теперь надстройки области задач и контентные надстройки из этого каталога доступны в диалоговом окне **Надстройки Office**. Для доступа к ним выберите**Мои надстройки** на вкладке **Вставка**, а затем нажмите **Моя организация**.

## <a name="end-user-experience-with-the-add-in-catalog"></a>Работа пользователей с каталогом надстроек

Пользователь может получить доступ к каталогу надстроек в приложении Office, выполнив указанные ниже действия.

1. В приложении Office выберите **Файл** > **Параметры** > **Центр управления безопасностью** > **Параметры центра управления безопасностью** > **Доверенные каталоги надстроек**.
    
2. Укажите URL-адрес _родительского семейства веб-сайтов SharePoint_ для каталога надстроек. 
    
    Предположим, что URL-адрес каталога надстроек Office такой:
    
    - `https:// _domain_ /sites/ _AddinCatalogSiteCollection_ /AgaveCatalog`
    
    Укажите только URL-адрес родительского семейства веб-сайтов:
    
    - `https:// _domain_ /sites/ _AddinCatalogSiteCollection_`
    
3. Закройте приложение Office и снова запустите его. Каталог надстроек будет доступен в диалоговом окне **Надстройки Office**.

Кроме того, администратор может указать каталог надстроек Office в SharePoint с помощью групповой политики. Дополнительные сведения см. в разделе [Использование групповой политики для управления возможностью установки и использования пользователями надстроек Office](https://technet.microsoft.com/ru-ru/library/jj219429.aspx#BKMK_GP) на сайте TechNet.
