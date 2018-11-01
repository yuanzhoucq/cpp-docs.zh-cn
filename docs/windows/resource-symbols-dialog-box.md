---
title: 资源符号对话框 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resourcesymbols
helpviewer_keywords:
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
ms.openlocfilehash: 156b531bfcedca70c930d77773d3a308735735f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483507"
---
# <a name="resource-symbols-dialog-box-c"></a>资源符号对话框 （c + +）

**资源符号**c + + 对话框允许您添加新的资源符号、 更改显示，或跳到源代码中正在使用的符号的位置的符号。

- **名称**

   显示符号的名称。 有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)。

- **值**

   显示符号的数值。 有关详细信息，请参阅[符号值限制](../windows/symbol-value-restrictions.md)。

- **在使用中**

   选中后，指定符号正由一个或多个资源使用。 “使用者”框中列出一个或多个资源。

- **显示只读符号**

   选定后，显示只读资源。 默认情况下**资源符号**对话框显示可修改的资源显示在资源脚本文件中，但选择此选项，则可修改的资源显示为粗体文本和纯文本中显示只读资源。

- **通过使用**

   显示使用符号列表中所选符号的一个或多个资源。 若要对于给定的资源移动到编辑器中，选择中的资源**使用者**框，然后单击**查看使用**。 有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。

- **新建**

   此时将打开**新符号**对话框中，这样就可以定义名称，如有必要，新的符号资源标识符的值。 有关详细信息，请参阅[创建新符号](../windows/creating-new-symbols.md)。

- **更改**

   此时将打开**更改符号**对话框中，以便您可以更改名称或符号值。 如果符号针对的是使用中的控件或资源，则仅可从相应的资源编辑器更改此符号。 有关详细信息，请参阅[更改未赋值符号](../windows/changing-unassigned-symbols.md)。

- **查看使用**

   打开包含相应资源编辑器中的符号的资源。 有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[查看资源符号](../windows/viewing-resource-symbols.md)