---
title: 为工具栏按钮创建工具提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor, creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27f4c5e3da313352358223de1499ef379db02bd7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647773"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button"></a>为工具栏按钮创建工具提示
### <a name="to-create-a-tool-tip"></a>若要创建的工具提示  
  
1.  选择工具栏上的按钮。  
  
2.  在中[属性窗口](/visualstudio/ide/reference/properties-window)，在**提示**属性字段中，添加按钮状态栏; 的消息显示后的说明，添加`\n`和工具提示名称。  
  
 工具提示的常见示例是**打印**按钮**写字板**:  
  
 1. 打开**写字板**。  
  
 2. 鼠标指针悬停**打印**工具栏按钮。  
  
 3. 请注意，word`Print`现在浮动的鼠标指针下。  
  
 4. 查看状态栏 (最底部**写字板**窗口)-请注意，它现在显示的文本`Prints the active document`。  
  
 `Print`中**第 3 步**是"工具提示名称"，并`Prints the active document`从**第 4 步**是"的状态栏按钮描述"。  
  
 如果你想使用此效果**工具栏**编辑器中，设置**提示**属性设置为`Prints the active document\nPrint`。  
  
> [!NOTE]
>  您可以使用提示文本编辑[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [创建、 移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)