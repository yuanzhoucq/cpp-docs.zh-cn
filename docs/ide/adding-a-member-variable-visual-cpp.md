---
title: 添加成员变量 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa2a8ef8f7bcdc2d90893acdad98705c9588a5d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325726"
---
# <a name="adding-a-member-variable--visual-c"></a>添加成员变量 (Visual C++)
可以使用类视图向类添加成员变量。 成员变量可以是[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)，也可以是泛型。 数据成员变量向导专门采用相关信息并使用其将元素插入源文件中的适当位置。 可以从[资源视图](../windows/resource-view-window.md)中的[对话框编辑器](../windows/dialog-editor.md)或[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)添加成员变量。  
  
> [!NOTE]
>  设计和实现对话框时，可能会发现使用对话框编辑器添加对话框控件，然后实现控件的成员变量更为有效。  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>使用添加成员变量向导在资源视图中添加对话框控件的成员变量  
  
1.  在资源视图中，展开项目节点和对话框节点，显示项目的对话框列表。  
  
2.  双击要向其添加成员变量的对话框，在对话框编辑器中将其打开。  
  
3.  在对话框编辑器中显示的对话框中，右键单击要向其添加成员变量的控件。  
  
4.  在快捷菜单上，单击“添加变量”以显示[添加成员变量向导](../ide/add-member-variable-wizard.md)。  
  
    > [!NOTE]
    >  “控件 ID”中已提供默认值。  
  
5.  在相应向导框中提供信息。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)，了解更多信息。  
  
6.  单击“完成”，即可将定义和实现代码添加到项目并关闭向导。  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>使用添加成员变量向导从类视图中添加成员变量  
  
1.  在[“类视图”](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，展开项目节点，显示项目中的类。  
  
2.  右键单击要向其添加变量的类。  
  
3.  在快捷菜单上，单击“添加”，然后单击“添加变量”以显示添加成员变量向导。  
  
4.  在相应向导框中提供信息。 请参阅[添加成员变量向导](../ide/add-member-variable-wizard.md)，了解详细信息。  
  
5.  单击“完成”，即可将定义和实现代码添加到项目并关闭向导。  
  
## <a name="see-also"></a>请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)