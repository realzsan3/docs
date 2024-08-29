# 如何调试 Firefly III？

如果您认为在 Firefly III 中发现了漏洞，或者您在使用数据导入器时需要帮助，您可以启用调试模式。在调试模式下，您可以确切查看错误是什么。 这在尝试找到错误源时会非常有用。

## 如何启用调试模式？

### Firefly III

#### 自主托管

当您自己托管 Firefly III 时，请打开您的 `.env` 文件并找到以下行：

* 以 `APP_DEBUG` 开头的行。将其更改为 `APP_DEBUG=true`
* 以 `APP_LOG_LEVEL` 开头的行。将其更改为 `APP_LOG_LEVEL=debug`
* 以 `LOG_CHANNEL` 开头的行。将其更改为 `LOG_CHANNEL=stack`

转到目录 `/firefly-iii/storage/logs`。删除除 `.gitignore` 以外的所有文件。

这将启用调试日志记录和调试模式。

#### Docker

当您使用 Docker 时，请使用以下参数重新启动容器：

```text
-e APP_DEBUG=true -e APP_LOG_LEVEL=debug -e LOG_CHANNEL=stack
```

### 数据导入器

#### 自主托管

当您自己托管数据导入器时，请打开您的 `.env` 文件并找到以下行：

* 以 `APP_DEBUG` 开头的行。将其更改为 `APP_DEBUG=true`
* 以 `LOG_LEVEL` 开头的行（如果尚未设置）。将其更改为 `LOG_LEVEL=debug`
* 以 `LOG_CHANNEL` 开头的行。将其更改为 `LOG_CHANNEL=stack`

转到目录 `/data-importer/storage/logs`。删除除 `.gitignore` 以外的所有文件。

这将启用调试日志记录和调试模式。

#### Docker

当您使用 Docker 时，请使用以下参数重新启动容器：

```text
-e APP_DEBUG=true -e APP_LOG_LEVEL=debug -e LOG_CHANNEL=stack
```

这将启用调试日志记录和调试模式。

## 我可以在哪里找到日志？

### 自主托管

检查文件夹 `storage/logs` 以获取每日日志文件流。

### Docker

运行以下命令以“tail” 日志并查看正在发生的事情：

```bash
docker container logs -f CONTAINER
```

`CONTAINER` 变量因人而异，但在许多情况下它是 `firefly-iii-app-1` 或 `data-importer-1`。

## 如何安全地提交调试信息？

许多数据文件包含私人信息。您应该**永远不要**在 GitHub 上共享这些文件。 它们很难删除。

!!! warning "上传文件到 GitHub"
    不要直接将 CSV 文件或 CAMT.053 上传到 GitHub，除非事先对其进行审查。

上传尽可能少的数据行或块来重现错误。 从剩余数据中删除个人信息包括（您的选择）：

- 将名称替换为假名；
- 将 IBAN 替换为 [虚假 IBAN](https://fakeiban.org/)；
- 将金额替换为虚假金额

!!! note "一致性很重要"
    尝试删除尽可能少的 data。 尝试一致地替换数据，例如始终将 IBAN“ABC”替换为相同的（虚假）IBAN。

您始终可以将您的数据文件亲自发送给我，邮箱地址是 [james@firefly-iii.org](mailto:james@firefly-iii.org)。这至少会将您的个人数据泄露给单个个人。我不能保证没有人会入侵我，但一旦问题关闭，您的文件就会被删除。
