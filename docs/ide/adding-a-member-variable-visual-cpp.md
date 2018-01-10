---
title: "添加成员变量 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.classes.member.variable
dev_langs: C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52d98e3eae6e468db7c2737efac8c2b7ab04abd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-member-variable--visual-c"></a>添加成员变量 (Visual C++)
可以将成员变量添加到使用类视图的类。 成员变量可用于[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)，也可以是泛型。 数据成员变量向导专门用于采用的相关信息并使用它来在适当的位置在源文件中插入元素。 你可以添加从的成员变量[对话框编辑器](../windows/dialog-editor.md)中[资源视图](../windows/resource-view-window.md)，或从[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)。  
  
> [!NOTE]
>  当你设计和实现对话框中，你可能会发现它更高效，先使用对话框编辑器添加对话框控件，然后实现的控件的成员变量。  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>在使用添加成员变量向导的资源视图中添加对话框控件的成员变量  
  
1.  在资源视图中，展开项目节点和对话框节点以显示项目的对话框的列表。  
  
2.  双击你想要添加要在对话框编辑器中打开它的成员变量对话框。  
  
3.  在对话框编辑器中显示的对话框中，右键单击你想要添加成员变量的控件。  
  
4.  在快捷菜单上，单击**添加变量**以显示[添加成员变量向导](../ide/add-member-variable-wizard.md)。  
  
    > [!NOTE]
    >  中已提供默认值**控件 ID**。  
  
5.  提供适当的向导框中的信息。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)有关详细信息。  
  
6.  单击**完成**以将定义和实现代码添加到项目并关闭向导。  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>若要从类视图使用添加成员变量向导添加的成员变量  
  
1.  在[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，展开项目节点以显示项目中的类。  
  
2.  右键单击你想要添加变量的类。  
  
3.  在快捷菜单上，单击**添加**，然后单击**添加变量**以显示添加成员变量向导。  
  
4.  提供适当的向导框中的信息。 请参阅[添加成员变量向导](../ide/add-member-variable-wizard.md)有关详细信息。  
  
5.  单击**完成**以将定义和实现代码添加到项目并关闭向导。  
  
## <a name="see-also"></a>请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)