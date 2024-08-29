# 如何管理预算

Firefly III 将预算作为一种强大的方式来管理您的财务。要开始使用，请访问 /budgets 页面并创建您的第一个预算。现在只需输入一个名称，其他什么都不需要。

要了解有关 Firefly III 中预算如何工作的更多信息，您应该阅读有关 Firefly III 中的预算。

当您从月头工作到月底时，Firefly III 的预算功能效果最佳。即使您每周或每年 13 次（4 周一次）获得报酬，这也适用。如果您在某个随机时间点获得报酬，这也适用。有关此方面的更多信息，请阅读 有关管理个人财务的说明。

![创建一个预算](../../../images/how-to/firefly-iii/finances/create-budget.png)

## 更改日期范围

预算的日期范围与您的视图范围相关联，您可以在首选项 > 布局中更改它。

## 基本预算

一旦您有了几个预算，您可以在创建交易时将它们链接到您的费用。另请参阅，如何组织交易。

这目前还不是很有用。因此，在 `/budgets` 页面上，您可以为预算设置最大金额。此金额适用于当前期间，对于大多数用户来说，适用于当前月份。每月预算是一种常见的组织财务方式。

![Overview](../../../images/how-to/firefly-iii/finances/budget-list.png)

## 自动化预算

!!! note
    我在这里谈论的是月份，但这也同样适用于周或季度。

当下一个月到来时，您的预算金额将消失，因为它们仅适用于上个月。您可以根据上个月的经验再次设置它们。
您还可以让 Firefly III 为您执行此操作。但是，这要求您知道 [如何运行 cron 作业](../advanced/cron.md).

仅在设置自动预算的第一个日期才会创建自动预算。如果 `cron` 作业没有在那个特定时间运行，则不会自动设置金额。因此，`cron` 作业应该每天运行。

| 自动预算期间 | 设置金额的时刻     |
|--------------------|--------------------------|
| Daily              | Every day                |
| Weekly             | Every Monday             |
| Monthly            | First day of the month   |
| Quarterly          | First day of the quarter |
| Every half year    | June 1st, December 1st   |
| Yearly             | First day of the year    |

您无法编辑或更改这些时刻。 它们被硬编码到 Firefly III 中。

![Basic auto budget](../../../images/how-to/firefly-iii/finances/auto-budget-1.png)

## 增长的预算

您还可以每月简单地向预算中添加资金。这样，它每个月都会增长。您可以从 25 开始，如果您不花任何钱，它每个月都会增长到 50、75 等。

![Growing auto budget](../../../images/how-to/firefly-iii/finances/auto-budget-2.png)

## 增长但纠正费用的预算

如果希望未使用的资金在下个月可用，可以使用之前的技巧。但是，如果您花费太多怎么办？想象一个每月 25 的预算。但是您决定花费 35。现在怎么办？使用这个小技巧，Firefly III 将把下个月的预算设置为 15 ，以纠正 10 的超支。

如果您花费的金额超过分配金额的两倍，Firefly III 将把下个月的预算设置为象征性的 1。如何处理取决于您。

![Also growing auto budget](../../../images/how-to/firefly-iii/finances/auto-budget-3.png)

## 混合周期

Firefly III 并不擅长处理混合周期。同时设置年度和每月预算很棘手。您可以通过在您的 `/preferences` 页面上更改视图范围，然后再次访问 `/budgets` 页面来执行此操作。如果预算的这些周期也重叠，您的费用将从两个金额中扣除。此外，Firefly III 不会自动计算每月应为多少年度预算。
