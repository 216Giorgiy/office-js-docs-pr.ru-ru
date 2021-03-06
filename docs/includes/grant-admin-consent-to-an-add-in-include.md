
> [!NOTE]
> Эта процедура необходима только для разработки надстройки. После развертывания в AppSource или каталоге надстроек пользователи будут самостоятельно добавлять ее в список доверенных. Этого не потребуется, если администратор даст согласие на ее использование в организации во время установки.

Выполните эту процедуру *после того, как* вы[зарегистрировали надстройку](../develop/register-sso-add-in-aad-v2.md).

1. В следующей строке, замените заполнитель "{application_ID}" идентификатором приложения, скопированным во время регистрации надстройки:  `https://login.microsoftonline.com/common/adminconsent?client_id={application_ID}&state=12345`

1. Вставив полученный URL-адрес в адресную строку браузера, перейдите по нему.

1. Войдите в область клиентов Office 365, используя учетные данные администратора.

1. Затем вам будет предложено предоставить надстройке разрешение на доступ к данным Microsoft Graph. Нажмите **Принять**.

1. Окно браузера/вкладка затем перенаправляется на**URL-адрес перенаправления**, который вы указали при регистрации надстройки. Если веб-приложение надстройки запущено, главная страница надстройки открывается в браузере; в противном случае вы получите ошибку 404. Но тот факт, что браузер попытался открыть домашнюю страницу, означает, что согласие на доступ было успешно предоставлено.

>[!NOTE]
>Мы рекомендуем эту процедуру в качестве наилучшей практики, если вы используете клиент разработчика приложений для Office 365. Однако, если вы предпочитаете, можно обойти надстройку SSO в процессе разработки и запросить у пользователя форму согласия. Для получения дополнительной информации см. [Загрузка на Windows](https://docs.microsoft.com/en-us/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins), а также [Загрузка на Office Online](https://docs.microsoft.com/en-us/office/dev/add-ins/testing/sideload-office-add-ins-for-testing).

