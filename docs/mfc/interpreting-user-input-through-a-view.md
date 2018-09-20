---
title: 通过视图解释用户输入 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 974324e296478f0ec36024d4427496d21255fbf7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421386"
---
# <a name="interpreting-user-input-through-a-view"></a>通过视图解释用户输入

视图的其他成员函数处理和解释所有用户输入。 通常将处理在视图类中定义消息处理程序成员函数：

- Windows[消息](../mfc/messages.md)生成的鼠标和键盘操作。

- [命令](../mfc/user-interface-objects-and-command-ids.md)从菜单、 工具栏按钮和快捷键。

这些消息处理程序成员函数解释为数据输入、 所选内容，或编辑，其中包括将数据移到和从剪贴板的以下操作：

- 鼠标移动和单击、 拖动和双击

- 击键

- 菜单命令

哪些 Windows 消息视图句柄取决于应用程序的需求。

[消息处理和映射主题](../mfc/message-handling-and-mapping.md)介绍如何将菜单项和其他用户界面对象分配给命令以及如何将命令绑定到处理程序函数。 [消息处理和映射主题](../mfc/message-handling-and-mapping.md)还介绍了 MFC 如何路由命令并将标准 Windows 消息发送到为它们包含处理程序的对象。

例如，你的应用程序可能需要实现直接绘制在视图中的鼠标。 Scribble 示例演示如何处理 WM_LBUTTONDOWN、 WM_MOUSEMOVE 和 WM_LBUTTONUP 消息，分别用于开始，继续，并结束绘制一条线段。 但是，你有时可能需要将与所选内容在视图中的鼠标单击解释。 视图的`OnLButtonDown`处理程序函数将确定用户是否已绘制或选择。 如果选择，该处理程序将会判断是否单击了该视图中的某个对象的边界内，如果是，更改显示器以显示为选中状态的对象。

您的视图也可能会处理某些菜单命令，如从编辑菜单来剪切、 复制、 粘贴或删除所选的数据使用剪贴板。 此类处理程序将调用剪贴板相关成员的一些类的函数`CWnd`要传输到或从剪贴板所选的数据项。

## <a name="see-also"></a>请参阅

[使用视图](../mfc/using-views.md)

