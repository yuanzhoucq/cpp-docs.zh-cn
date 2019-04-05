---
title: 预定义的符号 ID
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
ms.openlocfilehash: 5acaf9d470ce3d1cccad65bc8235cacfd7a56427
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024538"
---
# <a name="predefined-symbol-ids"></a>预定义的符号 ID

开始新项目时，根据项目类型预定义了一些符号 ID 供你使用。 这些符号 ID 支持 MFC 等各种库和项目类型。 它们表示通常包含于任何应用程序或硬件项（如鼠标或打印机）动作中的常见任务。

处理资源时，这些符号 ID 变得很重要。 它们可用于编辑快捷键对应表，其中一些已与虚拟键相关联。 它们还可以通过[属性窗口](/visualstudio/ide/reference/properties-window)。 可以将任何预定义的符号 Id 分配给新资源，或可以将快捷键分配给它们和 ID 会自动将与该密钥组合关联的符号与关联的功能。

库具有预定义将显示为项目的一部分的符号：

- [ATL 预定义的符号](../windows/atl-predefined-symbols.md)

- [MFC 预定义的符号](../windows/mfc-predefined-symbols.md)

- [Win32 预定义符号](../windows/win32-predefined-symbols.md)

> [!NOTE]
> 预定义的符号始终是只读的。

## <a name="requirements"></a>要求

Win32、MFC 或 ATL

## <a name="see-also"></a>请参阅

[资源标识符 （符号）](../windows/symbols-resource-identifiers.md)<br/>
[如何：创建符号](../windows/creating-new-symbols.md)<br/>
[如何：管理符号](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>