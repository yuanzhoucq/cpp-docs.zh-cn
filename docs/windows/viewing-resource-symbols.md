---
title: 查看资源符号 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
helpviewer_keywords:
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 4bcc06d9-7d36-486a-8a37-71da0541643c
ms.openlocfilehash: e61269261fc9172288f1edf58419009178c755d9
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763968"
---
# <a name="viewing-resource-symbols"></a>查看资源符号

**资源符号**c + + 对话框允许您添加新的资源符号、 更改显示，或跳到源代码中正在使用的符号的位置的符号。

对话框包含以下属性：

|属性|描述|
|---|---|
|**名称**|显示符号的名称。 有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)。|
|**值**|显示符号的数值。 有关详细信息，请参阅[符号值限制](../windows/symbol-value-restrictions.md)。|
|**在使用中**|选中后，指定符号正由一个或多个资源使用。 “使用者”框中列出一个或多个资源。|
|**显示只读符号**|选定后，显示只读资源。 默认情况下**资源符号**对话框显示可修改的资源显示在资源脚本文件中，但选择此选项，则可修改的资源显示为粗体文本和纯文本中显示只读资源。|
|**通过使用**|显示使用符号列表中所选符号的一个或多个资源。 若要对于给定的资源移动到编辑器中，选择中的资源**使用者**框，然后单击**查看使用**。 有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。|
|**新建**|此时将打开**新符号**对话框中，这样就可以定义名称，如有必要，新的符号资源标识符的值。 有关详细信息，请参阅[创建新符号](../windows/creating-new-symbols.md)。|
|**更改**|此时将打开**更改符号**对话框中，以便您可以更改名称或符号值。 如果符号针对的是使用中的控件或资源，则仅可从相应的资源编辑器更改此符号。 有关详细信息，请参阅[更改未赋值符号](../windows/changing-unassigned-symbols.md)。|
|**查看使用**|打开包含相应资源编辑器中的符号的资源。 有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。|

## <a name="to-view-resource-symbols"></a>查看资源符号

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 选择**资源符号**从要查看资源符号表中的快捷菜单**资源符号**对话框。

   > [!NOTE]
   > 若要查看预定义的符号，请**显示只读符号**复选框。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[符号：资源标识符](../windows/symbols-resource-identifiers.md)