---
title: 编辑快捷键对应表 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 56e24efb-d06b-4ed9-8915-1f99f725e247
ms.openlocfilehash: dfa0c26132378bcbe8a7f5203351134d91746aa7
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232170"
---
# <a name="editing-accelerator-tables-c"></a>编辑快捷键对应表 （c + +）

在 c + + 项目中，可以直接使用就地编辑中编辑快捷键对应表**Accelerator**编辑器。

下面的过程涉及到使用标准属性页，但是，就地编辑和属性页面方法都具有相同的结果。 所做的更改使用属性页或使用就地编辑将立即反映在快捷键对应表中。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

## <a name="to-edit-in-an-accelerator-table"></a>在快捷键对应表中编辑

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 在表中选择一个条目，并选择以激活就地编辑。

1. 从下拉组合框中进行选择或就地输入以进行更改。

   - 有关[ID](id-property.md)，从选择列表或输入以进行编辑。

   - 有关[修饰符](../windows/accelerator-modifier-property.md)，从列表中选择。

   - 有关[密钥](../windows/accelerator-key-property.md)，从选择列表或输入以进行编辑。

   - 有关[类型](../windows/accelerator-type-property.md)，选择**ASCII**或**VIRTKEY**从列表中。

## <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在打开的快捷键对应表中查找项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 选择列标题可以按字母顺序排序的列的内容。 例如，选择**ID**快捷键对应表中按字母顺序显示所有 Id。

然后，可以浏览列表并找到该项。

## <a name="to-add-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 在快捷键对应表中右键单击并选择**新的加速器**从快捷菜单上或选择表底部的空行项。

1. 选择[ID](id-property.md)从 ID 中的下拉列表框或键入中的新 ID **ID**框。

1. 类型[键](../windows/accelerator-key-property.md)你想要用作快捷键或右键单击并选择**键入的下一步键**从快捷菜单来设置组合键 (**键入的下一个密钥**命令是也可从**编辑**菜单)。

1. 更改[修饰符](../windows/accelerator-modifier-property.md)并[类型](../windows/accelerator-type-property.md)，如果有必要。

1. 按 **Enter**。

   > [!NOTE]
   > 确保定义的所有快捷键都是唯一的。 您可以将多种组合键分配给相同 ID 而产生任何不良影响，例如， **Ctrl** + **P**并**F8**可以同时分配给 ID_PRINT。 但是，具有分配给多个 ID 会无法正常工作，例如，组合键**Ctrl** + **Z**分配给 ID_SPELL_CHECK 和 ID_THESAURUS。

## <a name="to-delete-an-entry-from-an-accelerator-table"></a>若要从快捷键对应表删除项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 选择要删除的项。 (按住**Ctrl**或**Shift**键并选择以选择多个条目。)

1. 右键单击并选择**删除**从快捷菜单 (或选择**删除**从**编辑**菜单)。

\- 或 -

- 按**删除**密钥。

## <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>将快捷键对应表项移动或复制到另一个资源脚本文件

1. 在这两个资源脚本文件中打开快捷键对应表。

1. 选择要移动的项。

1. 从**编辑**菜单中，选择**副本**或**剪切**。

1. 在目标资源脚本文件中选择一个项。

1. 从**编辑**菜单中，选择**粘贴**。

   > [!NOTE]
   > 还可以使用快捷键进行复制和粘贴。

## <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要更改多个快捷键的属性

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 选择你想要更改通过按下的快捷键**Ctrl**选择每个键。

1. 转到[属性窗口](/visualstudio/ide/reference/properties-window)和中所需的所选的加速器共享所有的值类型。

   > [!NOTE]
   > 每个修饰符值显示为一个布尔值属性中**属性**窗口。 如果您更改[修饰符](../windows/accelerator-modifier-property.md)中的值**属性**窗口中，快捷键对应表视为新修饰符对先前已存在任何修饰符的补充。 因此，如果设置任何修饰符的值，您将需要设置它们以确保每个快捷键共享相同的所有**修饰符**设置。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[快捷键编辑器](../windows/accelerator-editor.md)<br/>
[资源编辑器](../windows/resource-editors.md)
