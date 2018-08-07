---
title: 移动和复制菜单和菜单命令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands, copying on menus
- menu items, moving
- commands, moving on menus
- menu items, copying
ms.assetid: 1d8df535-9922-4579-a9c2-37aeac1856eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ccab1e53fcbb407b6af7683b7aaaef75b0bb9789
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606584"
---
# <a name="moving-and-copying-menus-and-menu-commands"></a>移动和复制菜单和菜单命令
可以使用拖放方法或使用快捷菜单（右击菜单）上的命令来移动或复制菜单和菜单命令。  
  
### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>使用拖放方法移动或复制菜单或菜单命令  
  
1.  拖动或复制要移到下列位置的项：  
  
    -   当前菜单上的新位置。  
  
    -   不同的菜单。 （可以通过在其他菜单上拖动鼠标指针来导航到这些菜单。）  
  
2.  当插入参考线显示所需位置时放下菜单命令。  
  
### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>使用快捷菜单命令移动或复制菜单或菜单命令  
  
1.  右键单击一个或多个菜单或菜单命令。  
  
2.  从快捷菜单中选择 **“剪切”** （移动）或 **“复制”**。  
  
3.  如果将项移动到另一个菜单资源或资源脚本文件， [请在其他窗口中打开它](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。  
  
4.  选择要将菜单或菜单命令移动或复制到的位置。  
  
5.  从快捷菜单中选择 **“粘贴”**。 被移动或复制的项放在选定项的前面。  
  
    > [!NOTE]
    >  还可以拖动、复制和粘贴到其他菜单窗口中的其他菜单中。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息以及 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
## <a name="requirements"></a>要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [菜单编辑器](../windows/menu-editor.md)