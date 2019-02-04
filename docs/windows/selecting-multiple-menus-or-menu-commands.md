---
title: 编辑多个菜单或菜单命令 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: b6f17897-2a40-4afd-97d4-a38b7661680b
ms.openlocfilehash: 45e2c4e97dc850b4d6fb13a5526911e4bd5caec2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703215"
---
# <a name="editing-multiple-menus-or-menu-commands"></a>编辑多个菜单或菜单命令

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-select-multiple-menu-commands"></a>选择多个菜单命令

可以选择多个菜单名称或要运行大容量操作，如删除或更改属性的菜单命令。

在按下**Ctrl**密钥，请选择菜单或所需的子菜单命令。

## <a name="to-move-and-copy-menus-and-menu-commands"></a>若要移动和复制菜单和菜单命令

可以使用拖放方法或使用快捷菜单（右击菜单）上的命令来移动或复制菜单和菜单命令。

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>使用拖放方法移动或复制菜单或菜单命令

1. 拖动或复制要移到下列位置的项：

   - 当前菜单上的新位置。

   - 不同的菜单。 （可以通过在其他菜单上拖动鼠标指针来导航到这些菜单。）

1. 当插入参考线显示所需位置时放下菜单命令。

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>使用快捷菜单命令移动或复制菜单或菜单命令

1. 右键单击一个或多个菜单或菜单命令。

1. 从快捷菜单中选择 **“剪切”** （移动）或 **“复制”**。

1. 如果要将项移动到另一个菜单资源或资源脚本文件，[在另一个窗口中打开它](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

1. 选择要将菜单或菜单命令移动或复制到的位置。

1. 从快捷菜单中选择 **“粘贴”**。 被移动或复制的项放在选定项的前面。

   > [!NOTE]
   > 还可以拖动、复制和粘贴到其他菜单窗口中的其他菜单中。

## <a name="to-delete-a-menu-or-menu-command"></a>若要删除菜单或菜单命令

1. 右键单击菜单名称或命令。

1. 从快捷菜单选择 **“删除”** 。

   > [!NOTE]
   > 同样，可以使用快捷菜单来执行其他操作，例如，复制、剪切、粘贴、插入新项、插入分隔符、编辑 ID、以弹出方式查看、检查助记键等。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[菜单编辑器](../windows/menu-editor.md)