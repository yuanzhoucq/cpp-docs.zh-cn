---
title: "添加事件处理程序 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.eventhandler.overview
dev_langs: C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 172a9c2dd7f2af941c9b0ae5d2600d2717d15b1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="adding-an-event-handler-visual-c"></a>添加事件处理程序 (Visual C++)
从资源编辑器中，你可以添加一个新的事件处理程序，或编辑现有事件处理程序，对话框框控件使用[事件处理程序向导](../ide/event-handler-wizard.md)。  
  
 你可以将事件添加到实现对话框框中使用的类[属性窗口](/visualstudio/ide/reference/properties-window)。 如果你想要将事件添加到对话框类以外的类，使用事件处理程序向导。  
  
### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>若要将事件处理程序添加到对话框控件  
  
1.  双击对话框资源中的[资源视图](../windows/resource-view-window.md)以打开对话框资源包含在控件[对话框编辑器](../windows/dialog-editor.md)。  
  
2.  右键单击你想要处理该通知事件的控件。  
  
3.  在快捷菜单上，单击**添加事件处理程序**以显示事件处理程序向导。  
  
4.  选择中的事件**消息类型**框以将添加到中选定的类**类列表**框。  
  
5.  接受默认名称中的**函数处理程序名称**框中，或提供你选择的名称。  
  
6.  单击**添加和编辑**以向项目添加事件处理程序并打开新的函数在文本编辑器，添加相应的事件处理程序代码。  
  
     如果选定的消息类型已经具有所选的类，事件处理程序**添加和编辑**不可用，和**编辑代码**可用。 单击**编辑代码**以打开现有的函数在文本编辑器。  
  
 或者，你可以将添加事件处理程序从[属性窗口](/visualstudio/ide/reference/properties-window)。 请参阅[对于对话框控件添加事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)有关详细信息。  
  
## <a name="see-also"></a>另请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)