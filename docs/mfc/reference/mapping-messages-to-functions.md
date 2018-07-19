---
title: 消息映射到函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 962a86139b7fdf8afac08e04e7b42240603b4374
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335521"
---
# <a name="mapping-messages-to-functions"></a>将消息映射到函数
属性窗口，可将消息处理程序 （MFC 用户界面类的成员函数） 绑定到应用程序的资源生成的消息。 它们使用[MFC 消息映射](../../mfc/messages-and-commands-in-the-framework.md)以创建绑定。  
  
 当你使用类视图创建从框架类之一派生的新类时，它自动添加一个完整且实用类标头 (.h) 和实现 (.cpp) 中指定的文件。  
  
> [!NOTE]
>  若要添加一个新类，不处理消息，请直接在文本编辑器中创建的类。  
  
### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>若要定义或删除消息处理程序使用属性窗口  
  
1.  在“类视图”中，单击此类。  
  
2.  在属性窗口中，单击**消息**按钮。  
  
    > [!NOTE]
    >  **消息**在类视图或源窗口中单击时选择的类名称时，按钮才可用。  
  
     如果你的项目具有一条消息的处理程序，则会在消息旁的右侧列中显示处理程序的名称。  
  
3.  如果消息没有处理程序，然后单击属性窗口来作为处理程序的建议的名称显示在右侧的列中的单元格\<添加 >*HandlerName*。 (例如，WM_TIMER 消息处理程序建议\<添加 >`OnTimer`)。  
  
4.  单击建议名称，为函数添加存根代码。  
  
5.  若要编辑消息处理程序，双击类视图中的消息和编辑源窗口中的代码。  
  
 若要删除的消息处理程序，请双击右列中的处理程序，然后选择\<删除 >*HandlerName*。 即注释掉函数的代码。  
  
## <a name="see-also"></a>请参阅  
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [对于对话框控件添加事件处理程序](../../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)
