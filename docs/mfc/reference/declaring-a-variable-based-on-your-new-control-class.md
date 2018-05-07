---
title: 声明一个变量基于新控件类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 677006d441c940f478b3d23744d1057667307e1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>声明基于新控件类的变量
一旦创建了 MFC 控件类，可以声明变量基于它。 若要为新的变量提供的上下文，必须打开对话框编辑器，并编辑想要使用可重用控件的对话框。 此外，对话框中必须已有与之关联的类。 有关使用对话框编辑器的信息，请参阅[对话框编辑器](../../windows/dialog-editor.md)。  
  
### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>若要声明变量基于可重用类  
  
1.  在编辑对话框中，将从拖到对话框控件工具栏中拖动与新控件的基类属于同一类型的控件。  
  
2.  将鼠标指针放在拖动的控件。  
  
3.  在按住 CTRL 键，双击该控件。  
  
     [添加成员变量](../../ide/add-member-variable-wizard.md)对话框随即出现。  
  
4.  在**访问**框中，选择你的控件的正确访问权限。  
  
5.  单击**控制变量**复选框。  
  
6.  在**变量名称**框中，键入一个名称。  
  
7.  下**类别**，单击**控件**。  
  
8.  在**控件 ID**列表中，选取你添加的控件。 **变量类型**列表应显示正确的变量类型和**控件类型**框应显示正确的控件类型。  
  
9. 在**注释**框中，添加你想要显示在代码中的任何注释。  
  
10. 单击 **“确定”**。  
  
## <a name="see-also"></a>请参阅  
 [将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)
