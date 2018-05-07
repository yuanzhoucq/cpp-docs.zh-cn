---
title: 通过视图解释用户输入 |Microsoft 文档
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
ms.openlocfilehash: 5e3ade658046ad789a92bce044d12e5a6e76f7ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="interpreting-user-input-through-a-view"></a>通过视图解释用户输入
视图的其他成员函数处理和解释所有用户输入。 通常，你将定义消息处理程序成员函数处理视图类中：  
  
-   Windows[消息](../mfc/messages.md)鼠标和键盘操作生成。  
  
-   [命令](../mfc/user-interface-objects-and-command-ids.md)从菜单、 工具栏按钮和快捷键。  
  
 这些消息处理程序成员函数解释为数据输入、 选择，或编辑，包括将数据移到和从剪贴板的下列操作：  
  
-   鼠标移动和单击、 拖动和双击  
  
-   击键  
  
-   菜单命令  
  
 哪些 Windows 消息视图句柄取决于应用程序的需求。  
  
 [消息处理和映射主题](../mfc/message-handling-and-mapping.md)说明如何将菜单项和其他用户界面对象分配给命令以及如何将命令绑定到处理程序函数。 [消息处理和映射主题](../mfc/message-handling-and-mapping.md)还说明如何 MFC 将传递命令并将标准 Windows 消息发送到为它们包含处理程序的对象。  
  
 例如，你的应用程序可能需要实施直接绘制在视图中的鼠标。 Scribble 示例演示如何处理`WM_LBUTTONDOWN`， `WM_MOUSEMOVE`，和`WM_LBUTTONUP`消息分别若要开始，继续，并结束在绘制一条直线段。 另一方面，你有时可能需要将为所选内容在视图中的鼠标单击解释。 视图的`OnLButtonDown`处理程序函数将确定用户是否已绘制或选择。 如果选择，该处理程序将确定单击是否在视图中的某个对象的边界内，并如果是这样，更改显示器以显示所选的对象。  
  
 你的视图还可以处理某些菜单命令，如从编辑菜单进行剪切、 复制、 粘贴，或删除所选的数据使用剪贴板。 此类处理程序将调用某些剪贴板相关成员函数的类`CWnd`要传输到或从剪贴板对所选的数据项。  
  
## <a name="see-also"></a>请参阅  
 [使用视图](../mfc/using-views.md)

