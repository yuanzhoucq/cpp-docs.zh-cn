---
title: 如何：创建符号（C++）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 1c69e8878885acd80c285691fb0861a476af03ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160510"
---
# <a name="how-to-create-symbols-c"></a>如何：创建符号（C++）

开始使用新项目时，您可能会发现，在创建要分配给它们的资源之前，可以方便地映射您需要的符号名称。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅[如何：创建资源](../windows/how-to-create-a-resource-script-file.md)。

使用 "**资源符号**" 对话框，可以添加新的资源符号，更改显示的符号，或跳到源代码中使用符号的位置。

此对话框包含以下属性：

|properties|说明|
|--------------------------|------------------------------------------|
|**名称**|显示符号的名称。<br/><br/>有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)。|
|**值**|显示符号的数值。<br/><br/>有关详细信息，请参阅[符号值限制](../windows/symbol-value-restrictions.md)。|
|**正在使用**|选中后，指定符号正由一个或多个资源使用。<br/><br/>资源在 "**使用者**" 框中列出。|
|**显示只读符号**|选定后，显示只读资源。<br/><br/>默认情况下，"**资源符号**" 对话框仅显示资源脚本文件中的可修改资源，但选中此选项后，可修改的资源以粗体文本显示，只读资源以纯文本格式显示。|
|**使用者**|显示使用符号列表中所选符号的一个或多个资源。<br/><br/>若要移动到给定资源的编辑器，请在 "**使用者**" 框中选择资源，然后选择 "**查看使用**"。|
|**新建**|打开 "**新建符号**" 对话框，您可以在其中定义新的符号资源标识符的名称和值（如果需要）。|
|**更改**|打开 "**更改符号**" 对话框，使用该对话框可以更改符号的名称或值。<br/><br/>如果符号针对的是使用中的控件或资源，则仅可从相应的资源编辑器更改此符号。 有关详细信息，请参阅[管理符号](../windows/changing-unassigned-symbols.md)。|
|**查看使用情况**|打开包含相应资源编辑器中的符号的资源。|

## <a name="create-symbols"></a>创建符号

### <a name="to-create-a-new-symbol"></a>创建新符号

1. 在 "**资源符号**" 对话框中，选择 "**新建**"。

1. 在 "**名称**" 框中，键入符号名称。

1. 接受分配的符号值，或在 "**值**" 框中键入新值。

1. 选择 **"确定"** 将新符号添加到符号列表。

> [!NOTE]
> 如果输入的符号名已存在，则会出现一个消息框，表明已定义具有该名称的符号。 不能定义两个或多个具有相同名称的符号，但是可以定义具有相同数值的不同符号。

## <a name="to-view-resource-symbols"></a>查看资源符号

在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中，右键单击 *.rc*文件，然后在 "**资源**符号" 对话框中选择 "**资源符号**" 以查看资源符号表。

> [!NOTE]
> 若要查看预定义的符号，请选中 "**显示只读符号**" 复选框。

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>打开给定符号的资源编辑器

浏览**资源符号**中的符号时，可能需要有关如何使用特定符号的详细信息。 "**查看使用**" 按钮提供了获取此信息的快速方法。

1. 在 "**名称**" 框中的 "**资源符号**" 对话框中，选择符号。

1. 在 "**使用者**" 框中，选择你感兴趣的资源类型。

1. 选择 "**查看使用**" 按钮。

   资源显示在适当的编辑器窗口中。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源标识符（符号）](../windows/symbols-resource-identifiers.md)<br/>
[如何：管理符号](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[预定义的符号 ID](../windows/predefined-symbol-ids.md)<br/>
