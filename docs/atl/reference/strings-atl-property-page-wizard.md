---
title: 字符串，ATL 属性页向导
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.strings
helpviewer_keywords:
- ATL Property Page Wizard, strings
ms.assetid: 00547db6-911f-49eb-92e1-2ba67079d4df
ms.openlocfilehash: 04178c435bbd0ca80e412efc39a1b736062d95e7
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706767"
---
# <a name="strings-atl-property-page-wizard"></a>字符串，ATL 属性页向导

::: moniker range="vs-2019"

ATL 属性页向导不适用于 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="<=vs-2017"

提供与属性页关联的文本。

- **标题**

   设置属性页的选项卡中显示的文本。

- **文档字符串**

   设置描述属性页的文本字符串。 此字符串可以显示在属性表对话框中。 属性框架可以使用状态栏或工具提示中的说明。 标准属性框架暂不使用此字符串。

- **帮助文件**

   设置用于描述如何使用属性页的帮助文件的名称。 此名称不得包含路径。 当用户按“帮助”时，框架打开目录中的帮助文件，此目录是在 CLSID 下属性页注册表项中的 HelpDir 密钥值中指定。

::: moniker-end

## <a name="see-also"></a>请参阅

[ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)<br/>
[ATL 属性页向导的“选项”](../../atl/reference/options-atl-property-page-wizard.md)
