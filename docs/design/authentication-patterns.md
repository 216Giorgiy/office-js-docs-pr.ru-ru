# <a name="authentication-patterns"></a>Шаблоны проверки подлинности

Чтобы получить доступ к функциям и инструментам надстроек, пользователям, возможно, придется зарегистрироваться или авторизоваться. Поля ввода имени пользователя и пароля или кнопки, запускающие процессы сторонней авторизации, представляют собой общие элементы управления интерфейсом при проверке подлинности. Простой и эффективный процесс проверки подлинности — важный первый шаг использования вашей надстройки пользователями.

## <a name="best-practices"></a>Рекомендации

|Правильно|Неправильно|
|:----|:----|
|Использовать проверку подлинности с единым входом (SSO) для аутентификации пользователей в вашей надстройке.|Сделать обязательным отдельный вход в надстройку (пользователи должны авторизоваться отдельно, не используя свою личную учетную запись Microsoft или учетную запись Office 365 (на работе или учебе)).|
|Перед авторизацией описать важность надстройки или продемонстрировать ее функциональность, не требуя создания учетной записи. |Быть готовым к тому, что пользователи будут авторизовываться, не понимая ценности и преимуществ надстройки.|
|Помогать пользователям пройти процесс аутентификации, разместив на каждом экране базовую, хорошо заметную кнопку. |Обращать внимание пользователей на второстепенные и третьестепенные задачи с помощью конкурирующих кнопок и кнопок с призывом к действию.|
|Использовать четкие ярлыки кнопок, описывающие конкретные задачи, например, «Войти» или «Создать учетную запись».   |Использовать неопределенные ярлыки кнопок, например, «Отправить» или «Начать», в процессе аутентификации пользователей.|
|Использовать диалоговое окно, чтобы сосредоточить внимание пользователей на формах проверки подлинности.    |Перегрузить свою панель задач с помощью первого запуска и форм проверки подлинности.|
|Найти небольшие элементы эффективности в процессе проверки подлинности, например, автоматическую фокусировку на полях ввода. |Добавить ненужные шаги в процесс взаимодействия, например, требование к пользователям нажимать на поля формы.|
|Предоставить пользователям возможность выхода из системы и повторной проверки подлинности.    |Заставить пользователей удалить надстройку, чтобы сменить пользователя.|

> [!NOTE]
> В настоящее время API единого входа поддерживается для Word, Excel, Outlook и PowerPoint в тестовом режиме. Дополнительные сведения о текущей поддержке API единого входа см. в статье [Наборы обязательных элементов API идентификации](https://dev.office.com/reference/add-ins/requirement-sets/identity-api-requirement-sets). Если вы работаете с надстройкой Outlook, обязательно включите современную проверку подлинности для клиента Office 365. Инструкции см. в [этой статье](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx).


## <a name="authentication-flow"></a>Процесс проверки подлинности
Если единый вход еще не доступен вашим пользователям, рассмотрите возможность использования альтернативного процесса проверки подлинности. Дайте пользователям возможность входа в систему напрямую с помощью вашей службы или поставщика идентификатора, например, Microsoft.

1. Представление первого запуска — Разместите свою кнопку входа в систему в виде четкой кнопки-призыва к действию в первом запуске надстройки.
![](../images/add-in-fre-value-placemat.png)

2. Диалоговое окно выбора поставщика идентификатора — Отобразите список поставщиков идентификационных данных, включая имя пользователя и пароль, если это применимо. Пользовательский интерфейс вашей надстройки может быть заблокирован, если открыто диалоговое окно проверки подлинности.
![](../images/add-in-auth-choices-dialog.png)



3. Вход поставщика идентификатора — У поставщика идентификатора будет собственный интерфейс. Microsoft Azure Active Directory позволяет настраивать страницы входа и панели доступа для обеспечения неизменного соответствия вашей службе. [Узнать больше](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/customize-branding).
![](../images/add-in-auth-identity-sign-in.png)

4. Ход выполнения — Указывает ход выполнения загрузки настроек и пользовательского интерфейса.
![](../images/add-in-auth-modal-interstitial.png)

> [!NOTE] 
> При использовании службы идентификации Microsoft у вас будет возможность использовать фирменную кнопку входа, цвет которой можно настроить (светлый или темный). Узнать больше.

## <a name="single-sign-on-authentication-flow"></a>Процесс проверки подлинности с единым входом
Проверка подлинности с единым входом все еще находится в режиме предварительного просмотра. Когда эта модель станет доступна в стандартном режиме, используйте ее для обеспечения максимального удобства пользователей. Для входа в вашу надстройку используется идентификатор пользователя в Office. Как следствие, пользователи проходят авторизацию только один раз. Это устраняет неудобства и облегчает работу ваших клиентов.

1. Когда надстройка будет установлена, пользователь увидит окно согласия, похожее на показанное ниже: ![](../images/add-in-auth-SSO-consent-dialog.png)
> [!NOTE]
> Издатель надстройки будет иметь контроль над логотипом, программными строками и областями разрешений, включенными в окно согласия. Пользовательский интерфейс предварительно настроен Microsoft.

2. Надстройка загрузится после того, как пользователь согласится. Она сможет извлекать и отображать любую необходимую пользовательскую информацию.
![](../images/add-in-ribbon.png)

## <a name="see-also"></a>См. также
- Узнайте больше о [разработке надстроек SSO](https://docs.microsoft.com/en-us/office/dev/add-ins/develop/sso-in-office-add-ins)