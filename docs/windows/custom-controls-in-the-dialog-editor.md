---
title: 自定义控件在对话框编辑器中 （c + +）
ms.date: 11/04/2016
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
ms.openlocfilehash: c48ad87948037fa843fdc16a016ae23bf139feb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677092"
---
# <a name="custom-controls-in-the-dialog-editor-c"></a>自定义控件在对话框编辑器中 （c + +）

对话框编辑器使您可以使用现有的"自定义"或"user"控件在对话框模板中。

> [!NOTE]
> 在这个意义上的自定义控件将不使用 ActiveX 控件相混淆。 ActiveX 控件有时被称为 OLE 自定义控件。 此外，不要混淆 Windows 在所有者绘制的控件与这些控件。

此功能旨在使您可以用而非由 Windows 提供的控件。 在运行时，该控件是一个窗口类 （不完全相同的 c + + 类） 与相关联。 相同的任务是更常见的方法是安装任何控件，如静态控件在对话框中。 然后在在运行时， [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数中，删除该控件并将其自己的自定义控件替换为。

这是旧技术。 今天被建议在大多数情况下编写的 ActiveX 控件或 Windows 公共控件的子类。

对于这些自定义控件，仅限于：

- 在对话框中设置的位置。

- 键入一个标题。

- 用于标识控件的 Windows 类 （应用程序代码必须使用此名称注册控件） 的名称。

- 键入一个 32 位十六进制值，该值设置控件的样式。

- 设置扩展的样式。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)