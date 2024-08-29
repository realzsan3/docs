# 如何使用循环交易

Firefly III 可以自动为您创建交易，如果它们遵循严格的日程安排，例如每月、每周或每年。

此功能要求您知道 如何运行 [cron 作业](../advanced/cron.md)。如果您已正确设置电子邮件，Firefly III 将自动向您发送所创建交易的概述。

## 循环交易的信息

循环交易需要元数据，例如标题和描述。您还必须说明循环交易是否处于活动状态以及您的规则是否应该适用。循环交易应该触发的第一个日期应该是将来的日期。

![Mandatory information for a recurring transaction.](../../../images/how-to/firefly-iii/finances/recurrence-mandatory.png)

重复可以设置为以下选项：

- Every day.
- Every week on day X.
- Every month on day n (1st, 20th).
- Every month on the x-th X-day.
- Every year on a specific date.

一些注意事项：

- 第 x 个 X 天意味着 Firefly III 将在每个月的第一个星期三或第三个星期一创建交易。
- 如果您创建的交易应在月底的第 29、30 或 31 天重复，如果月份不够长，Firefly III 将自动回退到前一天。

您可以让 Firefly III 跳过每 X 次出现。

如果交易的日期应该在周末重复，Firefly III 可以自动：

- 完全跳过交易。
- 相反，在之前的星期五创建交易。请注意，您的循环交易似乎提前一天触发。
- 相反，在之后的星期一创建交易。请注意，您的循环交易似乎延迟一天触发。
- 简单地在周末创建交易。

## 交易本身的信息

这些是您在正常交易中所期望的所有字段：

![Mandatory information for a recurring transaction.](../../../images/how-to/firefly-iii/finances/transaction-mandatory.png)

- 交易类型。
- 描述、金额（和货币）以及源账户和目标账户。

可选信息包括：

- 外币和金额，如果您愿意。
- 类别、预算、储蓄罐和标签。
如果您希望将账单链接到交易，请确保选中应用规则选项，并且新交易将匹配此规则。

## 限制
1. 您无法向循环交易添加动态金额。
2. 您无法创建拆分交易。
