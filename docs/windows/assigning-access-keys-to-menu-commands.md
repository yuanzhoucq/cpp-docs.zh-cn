---
title: 给菜单命令分配访问键 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], checking
- menus, shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics, adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics, uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44a21e5930d0d8f2fcaad79cc5cef5bc984ad8b5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857894"
---
# <a name="assigning-access-keys-to-menu-commands"></a>给菜单命令分配访问键
可以向菜单和菜单命令分配访问键（使用户可以使用键盘选择菜单的助记键）。  
  
### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>向菜单命令分配访问（快捷）键  
  
1.  在菜单名称或命令名称中的某个字母前输入与号 (**&**)，以将该字母指定为对应的访问键。 例如，在为 Microsoft Windows 编写的应用程序中，“&File”将 ALT+F 设置为 File 菜单的快捷键。  
  
     菜单项会提供一个可见提示，指出已向一个字母分配了快捷键。 与号后面的字母在出现时会带有下划线（取决于操作系统）。  
  
    > [!NOTE]
    >  通过右键单击菜单并从快捷菜单选择“检查助记键”  ，来确保菜单上的所有访问键都是唯一的。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [菜单编辑器](../windows/menu-editor.md)