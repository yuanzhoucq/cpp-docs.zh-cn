---
title: 为工具栏按钮创建工具提示 |Microsoft 文档
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
ms.openlocfilehash: 41c2fa538a7888a2f14ae34fde9133b2872d13ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871762"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button"></a>为工具栏按钮创建工具提示
### <a name="to-create-a-tool-tip"></a>若要创建工具提示  
  
1.  选择工具栏按钮。  
  
2.  在[属性窗口](/visualstudio/ide/reference/properties-window)中**提示**属性字段中，添加按钮状态栏; 的消息显示后的说明，添加 \n 和工具提示名称。  
  
 工具提示的常见示例是写字板中的打印按钮：  
  
 1. 打开写字板。  
  
 2. 将鼠标指针悬停**打印**工具栏按钮。  
  
 3. 请注意，单词打印现在为浮点下鼠标指针。  
  
 4. 查看状态栏 （在最写字板窗口底部）-请注意，它现在显示文本"将打印活动文档"。  
  
 在步骤 3 中的打印是"工具提示名称"，并且从第 4 步的打印活动文档是"的状态栏按钮 description"。  
  
 如果你想使用此效果**工具栏**编辑器中，你将设置**提示**属性**将打印活动文档 \n 打印**。  
  
> [!NOTE]
>  你可以编辑提示文本使用[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [创建、 移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)

