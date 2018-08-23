---
title: 将菜单命令与 MFC 应用程序中的状态栏文本关联 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars, associating menu items
- menus, status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9cb5e57d6c7020e0b89104dac87fa3cd08ea023
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583696"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>将菜单命令与 MFC 应用程序中的状态栏文本关联

你的应用程序可以为用户可能选择的每个菜单命令显示说明性文本。 为此，可将文本字符串分配给每个菜单命令使用**Prompt**属性中的**属性**窗口。 如果 [字符串表](../windows/string-editor.md) 中有一个字符串，其 ID 与命令相同，则当用户悬停在菜单项上方时，MFC 应用程序将在运行的应用程序的状态栏中自动显示此字符串资源。

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>若要将菜单命令与状态栏文本字符串相关联

1. 在 **“菜单”** 编辑器中，选择菜单命令。

2. 在 [属性窗口](/visualstudio/ide/reference/properties-window)的 **“提示”** 框中键入关联的状态栏文本。

## <a name="requirements"></a>要求

MFC

## <a name="see-also"></a>请参阅

[字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[将命令添加到菜单](../windows/adding-commands-to-a-menu.md)  
[菜单编辑器](../windows/menu-editor.md)