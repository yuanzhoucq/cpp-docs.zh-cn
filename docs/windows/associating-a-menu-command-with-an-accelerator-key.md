---
title: 将菜单命令与快捷键关联 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4f1aa4b80aec2e7c16485c08d2505695b21f4d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>将菜单命令与快捷键关联
你经常希望某一菜单命令和某一键盘组合可以发出相同的程序命令。 你可以通过使用“菜单”编辑器为该菜单命令和应用程序快捷键对应表中的条目分配相同的资源标识符，来达到这个目的。 接着你可以编辑该菜单命令的 [标题](../windows/menu-command-properties.md) ，以显示快捷键的名称。  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>将菜单命令与快捷键关联  
  
1.  在**“菜单”** 编辑器中，选择所需菜单命令。  
  
2.  在[“属性窗口”](/visualstudio/ide/reference/properties-window)中，向**“标题”** 属性添加快捷键的名称：  
  
    -   在菜单标题后面，输入制表符 (\t) 的转义序列，以使所有菜单的快捷键都左对齐。  
  
    -   输入修改键的名称（**CTRL**、 **ALT**或 **SHIFT**），后跟一个加号 (**+**) 和附加键的名称、字母或符号。  
  
         例如，若要将 **CTRL+O** 分配给**“文件”** 菜单上的 **“打开”** 命令，请修改该菜单命令的“标题”  ，以便它如下所示：  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         在你输入时，“菜单”编辑器中的菜单命令会进行更新以反映新标题。  
  
3.  在[“快捷键”](../windows/adding-an-entry-to-an-accelerator-table.md) 编辑器中 **创建快捷键对应表条目** 并向它分配与菜单命令相同的标识符。 使用你认为易于记住的组合键。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [将命令添加到菜单](../windows/adding-commands-to-a-menu.md)   
 [菜单编辑器](../windows/menu-editor.md)