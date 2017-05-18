---
title: "声明变量基于新控件类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables, control classes
- control classes, variables
- classes [C++], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: a5777019ca87616fbb7c6a0d27140b3fabbf7fde
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>声明基于新控件类的变量
一旦创建了 MFC 控件类，可以声明基于它的变量。 若要为新的变量提供上下文，必须打开对话框编辑器并编辑想要使用您的可重用控件的对话框。 此外，对话框中必须已具有与其相关联的类。 有关使用对话框编辑器的信息，请参阅[对话框编辑器](../../windows/dialog-editor.md)。  
  
### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>若要将基于可重用类的变量声明  
  
1.  在编辑时对话框中，将作为新控件的基类相同类型的控件上从拖到对话框控件工具栏。  
  
2.  将鼠标指针放在拖动的控件。  
  
3.  在按住 CTRL 键，双击该控件。  
  
     [添加成员变量](../../ide/add-member-variable-wizard.md)对话框随即出现。  
  
4.  在**访问**框中，选择正确的访问权限为您的控件。  
  
5.  单击**控制变量**复选框。  
  
6.  在**变量名**框中，键入一个名称。  
  
7.  在下**类别**，请单击**控件**。  
  
8.  在**控件 ID**列表中，选取你添加的控件。 **变量类型**列表应显示正确的变量类型和**控件类型**框应显示正确的控件类型。  
  
9. 在**注释**框中，添加要在代码中显示的注释。  
  
10. 单击“确定”。  
  
## <a name="see-also"></a>另请参阅  
 [消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)

