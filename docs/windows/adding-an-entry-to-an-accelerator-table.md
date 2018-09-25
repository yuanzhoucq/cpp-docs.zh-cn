---
title: 将条目添加到快捷键对应表 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e0017e0c4d5462ef985b70b44120ff20066f626
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391795"
---
# <a name="adding-an-entry-to-an-accelerator-table-c"></a>将条目添加到快捷键对应表 （c + +）

### <a name="to-add-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项

1. 在 c + + 项目中，通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在快捷键对应表中右键单击并选择**新的加速器**从快捷菜单上或单击表底部的空行项。

3. 选择[ID](id-property.md)从 ID 中的下拉列表框或键入中的新 ID **ID**框。

4. 类型[键](../windows/accelerator-key-property.md)你想要用作快捷键或右键单击并选择**键入的下一步键**从快捷菜单来设置组合键 (**键入的下一个密钥**命令是也可从**编辑**菜单)。

5. 更改[修饰符](../windows/accelerator-modifier-property.md)并[类型](../windows/accelerator-type-property.md)，如果有必要。

6. 按 Enter。

   > [!NOTE]
   > 确保定义的所有快捷键都是唯一的。 您可以将多种组合键分配给相同 ID 而产生任何不良影响，例如， **Ctrl** + **P**并**F8**可以同时分配给 ID_PRINT。 但是，具有分配给多个 ID 会无法正常工作，例如，组合键**Ctrl** + **Z**分配给 ID_SPELL_CHECK 和 ID_THESAURUS。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[编辑快捷键对应表](../windows/editing-accelerator-tables.md)<br/>
[快捷键编辑器](../windows/accelerator-editor.md)