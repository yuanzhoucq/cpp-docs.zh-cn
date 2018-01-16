---
title: "创建菜单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.menu
dev_langs: C++
helpviewer_keywords:
- mnemonics, associating menu items
- menus, associating commands with mnemonic keys
- menus, creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d5d600a168c93b663ebe446ddd912d98fee1b19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-menu"></a>创建菜单
> [!NOTE]
>  资源窗口在 Express 版本中不可用。  
  
### <a name="to-create-a-standard-menu"></a>创建标准菜单  
  
1.  从 **“视图”** 菜单单击 **“资源视图”** ，然后右键单击 **“菜单”** 标题并选择 **“添加资源”**。 选择 **“菜单”**。  
  
2.  选择菜单栏上的“新建项目”  框（包含“请在此处输入”的矩形）。  
  
     ![菜单编辑器中的新项框](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")  
新建项目框  
  
3.  键入新菜单的名称，例如“文件”。  
  
     键入的文本将同时出现在 **菜单** 编辑器 以及 **属性窗口** 中的 [“标题”](/visualstudio/ide/reference/properties-window)框中。 你可以在任一位置编辑新菜单的属性。  
  
     为菜单栏上的新菜单指定名称后，新项目框移到右边（允许你添加另一菜单），并且另一个新项目框在第一个菜单下面打开，以便可以向其添加菜单命令。  
  
     ![展开新项框](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")  
新项目框的焦点在键入菜单名称后转移  
  
    > [!NOTE]
    >  要在菜单栏上创建单项菜单，请将“弹出”属性设置为 False。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [菜单编辑器](../windows/menu-editor.md)