---
title: MFC ActiveX 控件向导的控件名称
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: eff7b537e7fe5c19d10cce8766557a3d1ff49342
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077509"
---
# <a name="control-names-mfc-activex-control-wizard"></a>MFC ActiveX 控件向导的控件名称

指定控件类和属性页类的名称、类型名称和控件的类型标识符。 除**简称**外，所有其他字段都可以单独编辑。 如果更改**短名称**文本，则更改将反映在此页中所有其他字段的名称中。 此命名行为旨在方便你在开发控件时可轻松识别所有名称。

- **短名称**

   提供控件的缩写名称。 默认情况下，此名称基于在 "**新建项目**" 对话框中提供的项目名称。 您提供的名称将确定类名称、类型名称和类型标识符，除非单独更改这些字段。

- **控件类名**

   默认情况下，control 类的名称基于短名称，`C` 作为前缀，`Ctrl` 作为后缀。 例如，如果控件的短名称为 `Price`，则 `CPriceCtrl`控件类名称。

- **控制 .h 文件**

   默认情况下，标头文件的名称基于短名称，`Ctrl` 作为后缀，`.h` 作为文件扩展名。 例如，如果控件的短名称为 `Price`，则标头文件名为 `PriceCtrl.h`。 此字段中的名称应与控件类名称匹配。

- **控件 .cpp 文件**

   默认情况下，标头文件的名称基于短名称，`Ctrl` 作为后缀，`.cpp` 作为文件扩展名。 例如，如果控件的短名称为 `Price`，则标头文件名为 `PriceCtrl.cpp`。 此字段中的名称应与标头名称匹配。

- **控件类型名称**

   默认情况下，控件类型的名称基于短名称，后跟 `Control`。 例如，如果控件的短名称为 `Price`，则 `Price Control`控件类类型名称。 如果更改此字段中的值，请确保名称指示继承。

- **控件类型 ID**

   设置控件类的控件类型 ID。 控件添加到项目时，会将此字符串写入注册表。 容器应用程序使用此字符串创建控件的实例。

   默认情况下，控件类型 ID 基于您在 "**新建项目**" 对话框中指定的项目名称和短名称。 此名称应与类型名称匹配。

   默认情况下，控件类型 ID 如下所示：

   *项目名称. 短名称*Ctrl. 1

   如果更改此对话框中的短名称，则控件类型 ID 将如下所示：

   *项目名称. NewShortName*Ctrl. 1

- **属性页类名**

   默认情况下，属性页类的名称基于短名称，`C` 作为前缀，`PropPage` 作为后缀。 例如，如果控件的短名称为 `Price`，则 `CPricePropPage`属性页类名称。 此名称应与控件类名称匹配，并追加 `PropPage`。

- **属性页文件**

   默认情况下，属性页标题文件的名称基于短名称，作为后缀，作为文件扩展名 `.h` `PropPage`。 例如，如果您的控件的短名称为 `Price`，则 `PricePropPage.h`属性页头文件名。 此名称应与类名匹配。

- **属性页 .cpp 文件**

   默认情况下，属性页实现文件的名称基于短名称，并以作为后缀的 `PropPage`，`.cpp` 作为文件扩展名。 例如，如果您的控件的短名称为 `Price`，则 `PricePropPage.cpp`属性页头文件名。 此名称应与头文件名匹配。

- **属性页类型名称**

   默认情况下，属性页类型名称基于短名称，后跟 `Property Page`。 例如，如果控件的短名称为 `Price`，则 `Price Property Page`属性页类型名称。 如果更改此字段中的值，请确保名称指示控件类。

- **属性页类型 ID**

   设置属性页类的 ID。 当控件应用到项目时，它会在注册表中写入此字符串。 容器应用程序使用此字符串创建控件的属性页的实例。

   默认情况下，属性页类型 ID 基于您在 "**新建项目**" 对话框中指定的项目名称和短名称。 此名称应与类型名称匹配。

   默认情况下，属性页类型 ID 如下所示：

   *项目名称. 短名称*属性页

   如果更改此对话框中的短名称，则属性页类型 ID 如下所示：

   *项目名称. NewShortName*属性页

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[应用程序设置, MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控件向导控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[为 Visual Studio C++ 项目创建的文件类型](../../build/reference/file-types-created-for-visual-cpp-projects.md)
