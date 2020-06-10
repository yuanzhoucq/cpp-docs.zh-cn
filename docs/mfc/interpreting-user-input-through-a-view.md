---
title: 通过视图解释用户输入
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: 43fb903fa169233ce532e41ecdf02c23ab6037c8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621451"
---
# <a name="interpreting-user-input-through-a-view"></a>通过视图解释用户输入

视图的其他成员函数会处理并解释所有用户输入。 通常会在视图类中定义消息处理程序成员函数来处理：

- 鼠标和键盘操作生成的 Windows[消息](messages.md)。

- 来自菜单、工具栏按钮和快捷键的[命令](user-interface-objects-and-command-ids.md)。

这些消息处理程序成员函数将以下操作解释为数据输入、选择或编辑，包括将数据移到剪贴板以及从剪贴板移出数据：

- 鼠标移动和单击、拖动和双击

- 敲击

- 菜单命令

视图处理哪些 Windows 消息取决于应用程序的需求。

[消息处理和映射主题](message-handling-and-mapping.md)说明了如何将菜单项和其他用户界面对象分配到命令，以及如何将命令绑定到处理程序函数。 [消息处理和映射主题](message-handling-and-mapping.md)还介绍了 MFC 如何路由命令并将标准 Windows 消息发送到包含它们的处理程序的对象。

例如，你的应用程序可能需要在视图中实现直接的鼠标绘图。 自由绘制示例显示了如何分别处理 WM_LBUTTONDOWN、WM_MOUSEMOVE 和 WM_LBUTTONUP 消息，以便开始、继续和结束绘制直线段。 另一方面，有时可能需要将视图中的鼠标单击解释为选择。 视图的 `OnLButtonDown` 处理程序函数将确定用户是否在绘制或选择。 如果选择，处理程序将确定单击是否在视图中某个对象的边界内，如果是，则更改显示以显示选定的对象。

视图还可以处理某些菜单命令，例如 "编辑" 菜单中的某些菜单命令，用剪贴板剪切、复制、粘贴或删除所选数据。 此类处理程序将调用类的某些与剪贴板相关的成员函数，以将选定的数据项 `CWnd` 传输到剪贴板或从剪贴板传输选定的数据项。

## <a name="see-also"></a>另请参阅

[使用视图](using-views.md)
