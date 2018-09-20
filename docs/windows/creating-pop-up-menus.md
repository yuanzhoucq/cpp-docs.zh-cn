---
title: 创建弹出菜单 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c66f7074269e99b35785299800665be48cebef9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415715"
---
# <a name="creating-pop-up-menus-c"></a>创建弹出菜单 （c + +）

[弹出菜单](../mfc/menus-mfc.md) 显示常用命令。 它们对指针的位置可以区分上下文。 在应用程序中使用弹出菜单需要先生成菜单，然后将菜单连接到应用程序代码。

创建菜单资源后，应用程序代码需要加载该菜单资源并使用[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)才会显示该菜单。 用户通过单击弹出菜单之外的位置关闭弹出菜单后，或用户单击某个命令后，该函数将返回。 如果用户选择一个命令，该命令消息将被发送到传递了其句柄的窗口。

### <a name="to-create-a-pop-up-menu"></a>创建弹出菜单

1. 使用空标题（不提供[标题](../windows/creating-a-menu.md) ） **创建菜单**。

2. [将菜单命令添加到新菜单](../windows/adding-commands-to-a-menu.md)。 将移动到空白菜单标题下的第一个菜单命令 (临时标题显示`Type Here`)。 键入 **标题** 和任何其他信息。

   对弹出菜单中的任何其他菜单命令重复此过程。

3. 保存菜单资源。

   > [!TIP]
   > 有关查看弹出菜单的详细信息，请参阅 [以弹出菜单方式查看菜单](../windows/viewing-a-menu-as-a-pop-up-menu.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[将弹出菜单连接到应用程序](../windows/connecting-a-pop-up-menu-to-your-application.md)<br/>
[菜单编辑器](../windows/menu-editor.md)