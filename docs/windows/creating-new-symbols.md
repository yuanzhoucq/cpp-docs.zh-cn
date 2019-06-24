---
title: 如何：创建符号 (C++)
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
ms.openlocfilehash: d03246d2c701961c824b55fb0cbb781ee3f65028
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344201"
---
# <a name="how-to-create-symbols-c"></a>如何：创建符号 (C++)

当你开始一个新的项目时，你可能会发现可以方便地创建将分配的资源之前需要的符号名称映射。

> [!NOTE]
> 如果你的项目尚未包含.rc 文件，请参阅[如何：创建资源](../windows/how-to-create-a-resource-script-file.md)。

**资源符号**对话框允许您添加新的资源符号、 更改显示，或跳到源代码中正在使用的符号的位置的符号。

对话框包含以下属性：

|属性|描述|
|--------------------------|------------------------------------------|
|**名称**|显示符号的名称。<br/><br/>有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)。|
|**值**|显示符号的数值。<br/><br/>有关详细信息，请参阅[符号值限制](../windows/symbol-value-restrictions.md)。|
|**在使用中**|选中后，指定符号正由一个或多个资源使用。<br/><br/>中列出的资源**由**框。|
|**显示只读符号**|选定后，显示只读资源。<br/><br/>默认情况下**资源符号**对话框显示可修改的资源显示在资源脚本文件中，但选择此选项，则可修改的资源显示为粗体文本和纯文本中显示只读资源。|
|**通过使用**|显示使用符号列表中所选符号的一个或多个资源。<br/><br/>若要对于给定的资源移动到编辑器中，选择中的资源**由**框，然后选择**查看使用**。|
|**新建**|此时将打开**新符号**对话框中，可用于定义名称，如有必要，新的符号资源标识符的值。|
|**更改**|此时将打开**更改符号**对话框中，您可以更改名称或符号值。<br/><br/>如果符号针对的是使用中的控件或资源，则仅可从相应的资源编辑器更改此符号。 有关详细信息，请参阅[管理符号](../windows/changing-unassigned-symbols.md)。|
|**查看使用**|打开包含相应资源编辑器中的符号的资源。|

## <a name="create-symbols"></a>创建符号

### <a name="to-create-a-new-symbol"></a>若要创建新符号

1. 在中**资源符号**对话框框中，选择**新建**。

1. 在中**名称**框中，键入符号名称。

1. 接受分配的符号值或键入新值中的**值**框。

1. 选择**确定**将新符号添加到符号列表。

> [!NOTE]
> 如果输入的符号名已存在，则会出现一个消息框，表明已定义具有该名称的符号。 不能定义具有相同名称的两个或多个符号，但是可以定义具有相同的数字值的不同符号。

## <a name="to-view-resource-symbols"></a>查看资源符号

在中[资源视图](how-to-create-a-resource-script-file.md#create-resources)，右键单击你 *.rc*文件，然后选择**资源符号**若要查看资源符号表中的**资源符号**对话框。

> [!NOTE]
> 若要查看预定义的符号，请**显示只读符号**复选框。

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>若要打开给定符号的资源编辑器

当您在浏览中的符号**资源符号**，您可以如何使用特定符号的详细信息。 **查看使用**按钮提供的快速方法来获取此信息。

1. 在中**资源符号**对话框中的**名称**框中，选择一个符号。

1. 在中**使用者**框中，选择你感兴趣的资源类型。

1. 选择**查看使用**按钮。

   资源显示在适当的编辑器窗口中。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源标识符（符号）](../windows/symbols-resource-identifiers.md)<br/>
[如何：管理符号](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[预定义的符号 ID](../windows/predefined-symbol-ids.md)<br/>