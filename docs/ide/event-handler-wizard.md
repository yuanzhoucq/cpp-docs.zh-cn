---
title: 事件处理程序向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 544ce4cd0f4ed9a7f3592e5ec1691fb3734b8772
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="event-handler-wizard"></a>事件处理程序向导
此向导将一个事件处理程序的对话框控件添加到所选的类。 如果添加事件处理程序从[属性窗口](/visualstudio/ide/reference/properties-window)，可以将其添加到实现对话框中的类。 请参阅[对于对话框控件添加事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)有关详细信息。  
  
 **命令名称**  
 标识所选的控件，为其添加事件处理程序。 此框不可用。  
  
 **消息类型**  
 显示为选定控件的当前可能的消息处理程序的列表。  
  
 **函数处理程序名称**  
 显示添加对事件进行处理的函数的名称。 默认情况下，名称基于消息类型和命令，前面预置"on"。 例如，按钮调用`IDC_BUTTON1`，消息类型`BN_CLICKED`显示函数处理程序名称`OnBnClickedButton1`。  
  
 **类列表**  
 显示可向其中添加事件处理程序的可用类。 所选的对话框中的类显示为红色。  
  
 **处理程序说明**  
 提供在选定的项的说明**消息类型**框。 此框不可用。  
  
 **添加和编辑**  
 将消息处理程序添加到选定的类或对象，，然后打开文本编辑器到新函数，因此你可以添加控件通知处理程序代码。  
  
 **编辑代码**  
 打开文本编辑器中对所选的现有函数，以便你可以添加或编辑控件通知处理程序代码。  
  
## <a name="see-also"></a>请参阅  
 [添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)