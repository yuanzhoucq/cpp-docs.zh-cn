---
title: 创建菜单 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: 438480032f1fe9208e406b4ee499267e42148a48
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702799"
---
# <a name="creating-a-menu-c"></a>创建菜单 （c + +）

> [!NOTE]
> **资源窗口**在 Express 版本中不可用。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-create-a-standard-menu"></a>创建标准菜单

1. 从**视图**菜单中，选择**资源视图**，然后右键单击**菜单**标题并选择**添加资源**。 选择 **“菜单”**。

1. 选择菜单栏上的“新建项目”  框（包含“请在此处输入”的矩形）。

   ![菜单编辑器中的新项框](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   新建项目框

1. 键入新菜单的名称，例如“文件”。

   键入的文本将同时出现在 **菜单** 编辑器 以及 **属性窗口** 中的 [“标题”](/visualstudio/ide/reference/properties-window)框中。 你可以在任一位置编辑新菜单的属性。

   为菜单栏上的新菜单指定名称后，新项目框移到右边（允许你添加另一菜单），并且另一个新项目框在第一个菜单下面打开，以便可以向其添加菜单命令。

   ![展开新项框](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   新项目框的焦点在键入菜单名称后转移

   > [!NOTE]
   > 若要在菜单栏上创建单项菜单，请设置**Popup**属性设置为**False**。

## <a name="to-insert-a-new-menu-between-existing-menus"></a>在现有菜单之间插入新菜单

选择现有的菜单名称并按**插入**密钥。 **新项**框插入到所选的项之前。

   \- 或 -

在菜单栏上右键单击并选择**插入新**从快捷菜单。

## <a name="to-add-commands-to-a-menu"></a>将命令添加到菜单

1. 创建菜单。

1. 选择菜单名，例如**文件**。

   每个菜单都将展开，并显示一个新项框让你输入命令。 例如，可以将命令添加**新建**，**打开**，并**关闭**到**文件**菜单。

1. 在新项框中，键入新菜单命令的名称。

   > [!NOTE]
   > 键入的文本将同时出现在 **菜单** 编辑器 以及 **属性窗口** 中的 [“标题”](/visualstudio/ide/reference/properties-window)框中。 你可以在任一位置编辑新菜单的属性。

   > [!TIP]
   > 你可以定义一个允许用户选择菜单命令的助记键（热键）。 输入与号 (`&`) 若要指定为助记键的某个字母前。 用户可以通过键入该字母来选择菜单命令。

1. 在中**属性**窗口中，选择菜单命令适用的属性。 有关详细信息，请参阅[菜单命令属性](../windows/menu-command-properties.md)。

1. 在中**提示符**框中**属性**窗口中，键入你想要在应用程序的状态栏中显示的提示字符串。

   此步骤中创建具有菜单命令创建与相同的资源标识符的字符串表中的项。

   > [!NOTE]
   > 提示只能应用于菜单项**Popup**的属性**True**。 例如，包含子菜单项的顶级菜单项可以有提示。 目的**提示**用于指示会发生什么情况是如果用户选择菜单项。

1. 按**Enter**完成菜单命令。

   将选定新项框，让你可以创建其他菜单命令。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[菜单编辑器](../windows/menu-editor.md)