---
title: MFC ActiveX 控件向导的控件名称
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: a1b310de8cd8fcab1d880738faa7bd8b5b7cef32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373318"
---
# <a name="control-names-mfc-activex-control-wizard"></a>MFC ActiveX 控件向导的控件名称

指定控件类和属性页类，类型名称的名称和类型为您的控件的标识符。 除**短名称**，可以单独编辑所有其他字段。 如果您更改的文本**短名称**，更改都反映在此页中的所有其他字段的名称。 此命名行为设计以使所有名称轻松地识别为你在开发您的控件。

- **短名称**

   提供控件的缩写的名称。 默认情况下，此名称基于中提供的项目名称**新的项目**对话框。 所提供的名称确定类名称、 类型名称和类型标识符，除非您单独更改这些字段。

- **控件类名**

   默认情况下，控件类的名称基于短名称，并使用`C`作为前缀和`Ctrl`作为后缀。 例如，如果您的控件的短名称是`Price`，控件类名是`CPriceCtrl`。

- **控件.h 文件**

   默认情况下，标头文件的名称基于短名称，并使用`Ctrl`作为后缀和`.h`作为文件扩展名。 例如，如果您的控件的短名称是`Price`，标头文件名称是`PriceCtrl.h`。 在此字段中的名称应与控件类名。

- **控件.cpp 文件**

   默认情况下，标头文件的名称基于短名称，并使用`Ctrl`作为后缀和`.cpp`作为文件扩展名。 例如，如果您的控件的短名称是`Price`，标头文件名称是`PriceCtrl.cpp`。 此字段中的名称应与匹配的标头名称。

- **控件类型名称**

   默认情况下，控件类型的名称为基础的短名称后, 跟`Control`。 例如，如果您的控件的短名称是`Price`，该控件类类型名称是`Price Control`。 如果更改此字段中的值，请确保该名称指示继承。

- **控件类型 ID**

   设置控件类的控件类型 ID。 添加到项目时，控件将该字符串写入到注册表。 容器应用程序使用此字符串来创建控件的实例。

   默认情况下，控件类型 ID 基于中指示的项目名称**新的项目**对话框中，和短名称。 此名称应与类型名称。

   默认情况下，控件类型 ID，如下所示出现：

   *ProjectName.ShortName*Ctrl.1

   如果更改此对话框中的短名称的控件类型 ID 将出现，如下所示：

   *ProjectName.NewShortName*Ctrl.1

- **属性页类名**

   默认情况下，属性页类的名称基于短名称，并使用`C`作为前缀和`PropPage`作为后缀。 例如，如果您的控件的短名称是`Price`，属性页类名称将是`CPricePropPage`。 该名称应与在控件类名称后追加`PropPage`。

- **属性页.h 文件**

   默认情况下，属性页标头文件的名称基于短名称，并以`PropPage`作为后缀和`.h`作为文件扩展名。 例如，如果您的控件的短名称是`Price`，属性页标头文件名称将是`PricePropPage.h`。 此名称应与类名称。

- **属性页.cpp 文件**

   默认情况下，属性页上实现文件的名称基于短名称，并以`PropPage`作为后缀和`.cpp`作为文件扩展名。 例如，如果您的控件的短名称是`Price`，属性页标头文件名称将是`PricePropPage.cpp`。 此名称应与标头文件名称。

- **属性页类型名称**

   默认情况下，属性页类型名称为基础的短名称后, 跟`Property Page`。 例如，如果您的控件的短名称是`Price`，属性页类型名称将是`Price Property Page`。 如果更改此字段中的值，请确保该名称指示的控件类。

- **属性页类型 ID**

   设置属性页类的 ID。 应用到项目时，该控件在注册表中写入此字符串。 容器应用程序使用此字符串来创建控件的属性页的实例。

   默认情况下，属性页类型 ID 基于中指示的项目名称**新的项目**对话框中，和短名称。 此名称应与类型名称。

   默认情况下，属性页类型 ID 如下所示：

   *ProjectName.ShortName*PropPage.1

   如果更改此对话框中的短名称的属性页类型 ID 将出现，如下所示：

   *ProjectName.NewShortName*PropPage.1

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[应用程序设置, MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控件向导控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[为 Visual C++ 项目创建的文件类型](../../build/reference/file-types-created-for-visual-cpp-projects.md)

