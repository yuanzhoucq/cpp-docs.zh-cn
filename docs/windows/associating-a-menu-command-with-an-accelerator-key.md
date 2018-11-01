---
title: 将菜单命令与快捷键 （c + +） 相关联
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: c68d391d1046ab1d1af2fcf54b43b25a7aa9a237
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478320"
---
# <a name="associating-a-menu-command-with-an-accelerator-key-c"></a>将菜单命令与快捷键 （c + +） 相关联

你经常希望某一菜单命令和某一键盘组合可以发出相同的程序命令。 执行此操作通过使用**菜单**编辑器将为该菜单命令和应用程序的快捷键对应表中的条目分配相同的资源标识符。 接着你可以编辑该菜单命令的 [标题](../windows/menu-command-properties.md) ，以显示快捷键的名称。

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>将菜单命令与快捷键关联

1. 在 **“菜单”** 编辑器中，选择所需菜单命令。

2. 在[“属性窗口”](/visualstudio/ide/reference/properties-window)中，向 **“标题”** 属性添加快捷键的名称：

   - 在菜单标题后面，输入制表符 (\t) 的转义序列，以使所有菜单的快捷键都左对齐。

   - 键入的修改键名称 (**Ctrl**， **Alt**，或**Shift**) 后跟一个加号 (**+**) 和名称、 字母，或其他键的符号。

       例如，若要将分配**Ctrl**+**O**到**打开**命令**文件**菜单中，修改的菜单命令**标题**，以便它如下所示：

        ```
        &Open...\tCtrl+O
        ```

       中的菜单命令**菜单**编辑器更新以反映新的标题，并在您键入。

3. 在[“快捷键”](../windows/adding-an-entry-to-an-accelerator-table.md) 编辑器中 **创建快捷键对应表条目** 并向它分配与菜单命令相同的标识符。 使用你认为易于记住的组合键。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[将命令添加到菜单](../windows/adding-commands-to-a-menu.md)<br/>
[菜单编辑器](../windows/menu-editor.md)