---
title: "将位图转换为工具栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d189395bbedff4d73cc690d454ddd07af4d109e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="converting-bitmaps-to-toolbars"></a>将位图转换为工具栏
可以通过将位图转换来创建一个新的工具栏。 从位图图形将转换为工具栏按钮图像。 位图通常包含一个位图，与每个按钮的一个映像若干按钮图像。 映像可以是任意大小;默认值为 16 像素宽的图像的高度。 你可以指定在按钮图像的大小[新建工具栏资源对话框](../windows/new-toolbar-resource-dialog-box.md)当选择从工具栏编辑器**映像**与图像编辑器中的菜单。  
  
### <a name="to-convert-bitmaps-to-a-toolbar"></a>若要将位图转换为工具栏  
  
1.  打开中的现有位图资源[图像编辑器](../windows/image-editor-for-icons.md)。 (如果位图尚不在.rc 文件中，右键单击.rc 文件中，选择**导入**从快捷菜单中，导航到你想要添加到你的.rc 文件，该位图，然后单击**打开**。)  
  
2.  从**映像**菜单上，选择**工具栏编辑器**。  
  
     [新建工具栏资源对话框](../windows/new-toolbar-resource-dialog-box.md)显示。 你可以更改的宽度和高度与位图匹配的图标图像。 工具栏编辑器中，然后显示工具栏图像。  
  
3.  若要完成转换，更改该命令**ID**按钮使用[属性窗口](/visualstudio/ide/reference/properties-window)。 键入新**ID**或选择**ID**从下拉列表。  
  
    > [!TIP]
    >  属性窗口包含标题栏中的图钉按钮。 单击此按钮启用或禁用窗口的自动隐藏。 若要快速循环通过所有工具栏按钮属性而无需重新打开各个属性窗口，关闭自动隐藏以便属性窗口保持不变。  
  
 此外可以通过更改新的工具栏上的按钮的命令 Id[属性窗口](/visualstudio/ide/reference/properties-window)。 编辑新的工具栏上的信息，请参阅[创建、 移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 惠?  
  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [创建新工具栏](../windows/creating-new-toolbars.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)

