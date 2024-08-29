# 如何对账

虽然越来越多的人使用网上银行，但许多用户仍然每周或每月通过邮件收到纸质银行对账单。Firefly III 具有一个“对账”视图，允许您验证您的交易是否与您的银行对账单完全匹配。这还可以帮助在将大量交易导入 Firefly III 后解决余额不正确的问题。

## 打开对账页面

从资产账户列表或单个资产账户页面打开页面。

从单个账户：

![The button is at the top of the chart](../../../images/how-to/firefly-iii/finances/reconcile-account-home.png)

从账户概述：

![The button is in the menu on the right](../../../images/how-to/firefly-iii/finances/reconcile-account-index.png)

## 开始对账

首先，输入日期范围并设置与银行对账单上显示的开户余额和结账余额。

![These dates and amounts must match your bank statement.](../../../images/how-to/firefly-iii/finances/reconcile-set-amounts.png)

例如：

* Start date: January 1st, 2018. Balance: € 120
* End date: January 31st, 2018. Balance: € 788

接下来，按 **开始对账** 继续。

Firefly III 将显示此范围内的交易，以及一些较早和较晚的交易。对于银行对账单上的每条交易行，请在 Firefly III 中找到匹配的交易，然后选中金额列旁边的框。您的目标是验证您的 Firefly III 交易与您的银行对账单完全匹配。查看整个对账单并检查 Firefly III 中的每笔交易。

- 如果您发现重复的交易，您可以单击交易描述以查看交易，然后从该页面删除交易。删除后，您将返回到对账页面。先前选中的交易将再次选中。
- 如果您发现不正确的交易，您可以单击“编辑”铅笔图标进入编辑模式。编辑后，您将返回到对账视图。先前选中的交易将再次选中。

对账完成后，请查看屏幕顶部“对账选项”部分中的金额。

### “对账选项”下的金额小于零

这意味着您的 Firefly III 资产账户中的余额应该比实际少。查找重复交易或不正确的金额并根据需要进行更正。当您按下“存储对账”按钮时，您可以让 Firefly III 创建一个自动交易来纠正此差异。

![When your account is too low on funds, you can allow Firefly III to create a corrective transaction.](../../../images/how-to/firefly-iii/finances/reconcile-negative-action.png)

### “对账选项”下的金额大于零

这意味着您的 Firefly III 资产账户中的余额应该比实际多。查找缺少的交易或不正确的金额并根据需要进行更正。当您按下“存储对账”按钮时，您可以让 Firefly III 创建一个自动交易来纠正此差异。

![When your account is too full, you can allow Firefly III to create a corrective transaction.](../../../images/how-to/firefly-iii/finances/reconcile-positive-action.png)

### “对账选项”下的金额正好为零！

恭喜！这意味着您的 Firefly III 交易与您的银行对账单完全匹配。您现在可以按“存储对账”以将选中的交易标记为已对账。

![When there is no mismatch between your bank statements and Firefly III, you don't need to do anything.](../../../images/how-to/firefly-iii/finances/reconcile-neutral-action.png)
