---
title: 对话框编辑器中的自定义控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- Custom Control
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [Visual Studio], dialog boxes
- custom controls [Visual Studio]
- dialog box controls, custom (user) controls
- Dialog editor, custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2c2bca249958e4d25ab5377540525da34802ac04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880239"
---
# <a name="custom-controls-in-the-dialog-editor"></a>对话框编辑器中的自定义控件
对话框编辑器，可使用现有的"自定义"或"用户"对话框模板中的控件。  
  
> [!NOTE]
>  在这个意义上的自定义控件将不会与 ActiveX 控件混淆。 ActiveX 控件有时被称为 OLE 自定义控件。 此外，不要将这些控件与 Windows 中的所有者描述控件相混淆。  
  
 此功能旨在让你使用除提供的 Windows 之外的控件。 在运行时，控件所关联的窗口类 （不与相同的 c + + 类）。 完成相同任务的更常用方法是安装任何控件，如静态控件，在对话框中。 然后在在运行时， [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数中，删除该控件并将其替换为你自己的自定义控件。  
  
 这是旧技术。 今天建议您在大多数情况下编写一个 ActiveX 控件或 Windows 公共控件子类化。  
  
 对于这些自定义控件，你将限于：  
  
-   在对话框中设置的位置。  
  
-   键入标题。  
  
-   标识控件的窗口类 （应用程序代码必须使用此名称注册控件） 的名称。  
  
-   键入一个 32 位十六进制值，设置控件的样式。  
  
-   设置扩展的样式。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)

