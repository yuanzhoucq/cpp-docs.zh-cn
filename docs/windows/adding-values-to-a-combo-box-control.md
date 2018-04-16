---
title: "将值添加到组合框控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [Visual Studio], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- controls [C++], testing values in combo boxes
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9125ad60648f6f867e1214763a6af164d0239a04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-values-to-a-combo-box-control"></a>向组合框控件添加值
可以将值添加到组合框控件中，只要你有打开的对话框编辑器中。  
  
> [!TIP]
>  它是一个好办法将所有值都添加到组合框*之前*大小的框中对话框编辑器中，或可能会截断应组合控件中显示的文本。  
  
#### <a name="to-enter-values-into-a-combo-box-control"></a>若要在组合框控件中输入值  
  
1.  通过单击选择组合框控件。  
  
2.  在[属性窗口](/visualstudio/ide/reference/properties-window)，向下滚动到**数据**属性。  
  
    > [!NOTE]
    >  如果您要显示按类型分组的属性**数据**出现在**杂项**属性。  
  
3.  在值区域内单击**数据**属性并键入你的数据值，由分号分隔。  
  
    > [!NOTE]
    >  不要将值之间的空间，因为空间妨碍下拉列表中按字母顺序排列。  
  
4.  单击**Enter**在完成添加值时。  
  
 有关增大组合框的下拉部分的信息，请参阅[设置组合框及其下拉列表大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。  
  
> [!NOTE]
>  无法将值添加到使用此过程的 Win32 项目 (**数据**属性将灰显，对于 Win32 项目)。 由于 Win32 项目不会将此功能添加的库，你必须以编程方式添加到带有 Win32 项目的组合框的值。  
  
#### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>若要在组合框中测试的值的外观  
  
1.  在输入中的值后**数据**属性，单击**测试**按钮上[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。  
  
     请尝试整个值列表中向下滚动。 显示的值完全与键入的**数据**属性窗口中的属性。 没有拼写或大小写检查。  
  
     按 ESC 键返回到对话框编辑器。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)

