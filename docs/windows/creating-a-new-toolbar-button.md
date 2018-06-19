---
title: 创建新的工具栏按钮 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor, creating buttons
- toolbar buttons (in Toolbar editor), button image
- toolbar buttons (in Toolbar editor), creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d883fbb34fe45be2ad84860ea7564350346749f2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873022"
---
# <a name="creating-a-new-toolbar-button"></a>创建新的工具栏按钮
### <a name="to-create-a-new-toolbar-button"></a>若要创建新的工具栏按钮  
  
1.  在[资源视图](../windows/resource-view-window.md)展开资源文件夹 (如 Project1.rc)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  展开**工具栏**文件夹，然后选择要编辑的工具栏。  
  
3.  将 ID 分配给工具栏右侧的空白按钮。 你可以通过编辑来实现**ID**中的属性[属性窗口](/visualstudio/ide/reference/properties-window)。 例如，你可能想要为工具栏按钮指定为菜单选项相同的 ID。 在这种情况下，使用下拉列表框选择**ID**的菜单选项。  
  
     -或-  
  
     选择空白按钮 （在工具栏视图窗格中） 工具栏右侧并开始绘制。 分配默认按钮命令 ID (ID_BUTTON\<n >)。  
  
 你还可以复制并粘贴到为新按钮的工具栏上的映像。  
  
#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要为按钮添加到工具栏的图像  
  
1.  在[资源视图](../windows/resource-view-window.md)，工具栏上双击以打开它。  
  
2.  接下来，打开你想要将添加到你工具栏的图像。  
  
    > [!NOTE]
    >  如果在 Visual Studio 中打开的图像，它将在图像编辑器中打开。 你可以在其他图形程序中打开的图像。  
  
3.  从**编辑**菜单上，选择**复制**。  
  
4.  通过单击其选项卡顶部的源窗口切换到你的工具栏。  
  
5.  从**编辑**菜单上，选择**粘贴**。  
  
     图像将显示在工具栏上，为新按钮。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>要求  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [工具栏按钮属性](../windows/toolbar-button-properties.md)   
 [创建、 移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)

