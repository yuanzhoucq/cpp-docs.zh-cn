---
title: 将菜单命令 （c + +） 关联
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: f72fe5de3ef29b9575ef1a3138d4d114d7470fee
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703033"
---
# <a name="associating-menu-commands-c"></a>将菜单命令 （c + +） 关联

你经常希望某一菜单命令和某一键盘组合可以发出相同的程序命令。 通过使用在发出相同的命令**菜单**编辑器将为该菜单命令和应用程序的快捷键对应表中的条目分配相同的资源标识符。 接着你可以编辑该菜单命令的 [标题](../windows/menu-command-properties.md) ，以显示快捷键的名称。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>将菜单命令与快捷键关联

1. 在 **“菜单”** 编辑器中，选择所需菜单命令。

1. 在[“属性窗口”](/visualstudio/ide/reference/properties-window)中，向 **“标题”** 属性添加快捷键的名称：

   - 在菜单标题后面，输入制表符 (\t) 的转义序列，以使所有菜单的快捷键都左对齐。

   - 键入的修改键名称 (**Ctrl**， **Alt**，或**Shift**) 后跟一个加号 (**+**) 和名称、 字母，或其他键的符号。

       例如，若要将分配**Ctrl**+**O**到**打开**命令**文件**菜单中，修改的菜单命令**标题**，使其类似于以下文本：

        ```
        &Open...\tCtrl+O
        ```

       中的菜单命令**菜单**编辑器更新以反映新的标题，并在您键入。

1. 在[“快捷键”](../windows/adding-an-entry-to-an-accelerator-table.md) 编辑器中 **创建快捷键对应表条目** 并向它分配与菜单命令相同的标识符。 使用你认为易于记住的组合键。

## <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>若要将菜单命令与状态栏 MFC 应用程序中的文本字符串相关联

MFC 应用程序可以为每个用户可能选择的菜单命令显示说明性文本。 通过将文本字符串分配给每个菜单命令使用显示的说明性文本**Prompt**属性中的**属性**窗口。 如果 [字符串表](../windows/string-editor.md) 中有一个字符串，其 ID 与命令相同，则当用户悬停在菜单项上方时，MFC 应用程序将在运行的应用程序的状态栏中自动显示此字符串资源。

1. 在 **“菜单”** 编辑器中，选择菜单命令。

1. 在 [属性窗口](/visualstudio/ide/reference/properties-window)的 **“提示”** 框中键入关联的状态栏文本。

> [!NOTE]
> 这一组步骤需要 MFC。

## <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>向菜单命令分配访问（快捷）键

在 c + + 项目中，可以向菜单和菜单命令分配访问键 （使用户可以用键盘选择菜单的助记键）。

输入与号 (`&`) 中的菜单名称或命令名称以该字母指定为相应的访问密钥的某个字母前。 例如，"& 文件"集**Alt**+**F**作为的快捷键**文件**为 Microsoft Windows 编写应用程序中的菜单。

   菜单项会提供一个可见提示，指出已向一个字母分配了快捷键。 与号后面的字母在出现时会带有下划线（取决于操作系统）。

   > [!NOTE]
   > 通过右键单击菜单并从快捷菜单选择“检查助记键”  ，来确保菜单上的所有访问键都是唯一的。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[菜单编辑器](../windows/menu-editor.md)<br/>
[将命令添加到菜单](../windows/adding-commands-to-a-menu.md)<br/>
[字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
