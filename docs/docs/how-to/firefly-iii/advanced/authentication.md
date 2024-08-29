# 如何使用不同的身份验证

默认情况下，Firefly III 使用一个基本系统，允许用户在本地注册和登录。这是基于用户的电子邮件地址。

另请参阅 [如何使 Firefly III 多用户](../features/multi-user.md)。

## Two-step authentication

双重身份验证或双因素身份验证 (2FA) 要求您输入额外的代码。这增加了安全性，即使您丢失了密码，您的帐户仍然受到保护。

您可以在您的个人资料中启用它。

![The button is shown in your list of accounts.](../../../images/how-to/firefly-iii/advanced/2fa-enable.png)

如果您启用 2FA，您还将看到八个备份代码，您应该保存这些代码，以防您丢失对身份验证应用程序的访问权限。

![The button is shown in your list of accounts.](../../../images/how-to/firefly-iii/advanced/2fa-codes.png)

要确认您的 2FA 设置，请从您的身份验证应用程序中提交两次代码。您可能需要等待 30 秒。在您的设置中，您将看到 2FA 的升级状态：

![Options for 2FA.](../../../images/how-to/firefly-iii/advanced/2fa-reset.png)

如果您丢失了对 2FA 数据的访问权限，任何有权访问数据库的人都可以将其关闭并让您重新登录。[请查看常见问题](../../../references/faq/firefly-iii/general.md)。

## 远程用户身份验证

Firefly III 支持 [RFC 3875](https://tools.ietf.org/html/rfc3875#section-4.1.11)，这意味着您的用户可以使用 `REMOTE_USER` 标头进行身份验证。当您启用此方法时，必须设置 Firefly III 前面的身份验证代理来处理用户的登录和身份验证。这使您可以使用高级登录方法，如硬件令牌、单点登录、指纹读取器等。一旦身份验证代理说您已登录，它将转发您到 Firefly III。

一个非常流行的工具可以做到这一点 [Authelia](https://www.authelia.com/docs/)。

!!! warning
    当 Firefly III 设置为远程用户身份验证时，它将绝对**不会**检查标头的有效性或内容。Firefly III 不会询问密码，也不会检查 MFA，什么都不会。所有身份验证都委托给身份验证代理，Firefly III 只是不再关心。

### 启用远程用户选项

要启用此功能，请将 `AUTHENTICATION_GUARD` 环境变量更改为 `remote_user_guard`。

将 `AUTHENTICATION_GUARD_HEADER` 设置为将包含用户标识符（通常是电子邮件地址或用户名）的 HTTP 标头。如果标识符不是电子邮件地址，请将 `AUTHENTICATION_GUARD_EMAIL` 设置为将包含用户电子邮件地址的 HTTP 标头。

### 工作原理

一旦您通过代理进行身份验证，Firefly III 将接收带有 `REMOTE_USER` 标头中的用户 ID 的请求。然后，Firefly III 将登录您。

### 意外空标头

作为故障排除步骤，请尝试将 `AUTHENTICATION_GUARD_HEADER` 环境变量设置为 `HTTP_REMOTE_USER`。  如果这不起作用，请取消设置 `AUTHENTICATION_GUARD_HEADER` 环境变量并进行以下更改。

该标头必须转发到 Firefly III。例如，将以下行添加到 `public/.htaccess`。

```
    RewriteCond %{HTTP:REMOTE_USER} .
    RewriteRule .* - [E=REMOTE_USER:%{HTTP:REMOTE_USER}]
```

当您使用 Docker 映像时，这不太理想，但如果标头被发送到您的反向代理而不是直接发送到 Firefly III，则可能需要进行这样的更改。

### 另一个远程用户标头

如果您能够自定义您的身份验证系统以向 Firefly III 发送除 `REMOTE_USER` 以外的标头，那么请将 `AUTHENTICATION_GUARD_HEADER` 环境变量设置为该标头的 PHP 名称。  例如，如果自定义标头是 `FFIII-User`，那么请将 `AUTHENTICATION_GUARD_HEADER` 设置为 `HTTP_FFIII_USER`。  使用自定义标头的另一个好处是，您不需要像上面提到的那样更改 `public/.htaccess` 文件。

Firefly III 使用电子邮件地址作为用户标识符。当您使用不执行此操作的外部身份验证保护时，Firefly III 无法向您发送电子邮件。

如果用户电子邮件地址也可以通过不同的 HTTP 标头获得，那么请将 `AUTHENTICATION_GUARD_EMAIL` 环境变量设置为该标头的 PHP 名称。  例如，如果自定义标头是 `FFIII-Email`，那么请将 `AUTHENTICATION_GUARD_EMAIL` 设置为 `HTTP_FFIII_EMAIL`
