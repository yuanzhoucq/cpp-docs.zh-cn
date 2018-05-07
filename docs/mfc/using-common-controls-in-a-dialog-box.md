---
title: 在对话框中使用公共控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c848cfa74363d871720f9ca269b114687aad9ecf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-common-controls-in-a-dialog-box"></a>在对话框中使用公共控件
Windows 公共控件可在[对话框](../mfc/dialog-boxes.md)，窗体视图、 记录视图和任何其他基于对话框模板的窗口。 以下过程有细微更改，同样适用于窗体。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-use-a-common-control-in-a-dialog-box"></a>在对话框中使用公共控件  
  
1.  将控件放在对话框模板[使用对话框编辑器](../mfc/using-the-dialog-editor-to-add-controls.md)。  
  
2.  向对话框类添加表示控件的成员变量。 在**添加成员变量**对话框中，选中**控制变量**并确保**控件**为选择**类别**。  
  
3.  如果此公共控件提供至程序的输入，则在对话框类中声明其他成员变量以处理这些输入值。  
  
    > [!NOTE]
    >  你可以添加在类视图中使用上下文菜单这些成员变量 (请参阅[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md))。  
  
4.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)对话框类，将设置为公共控件的初始条件。 通过使用在上一步中创建的成员变量，使用成员函数设置初始值和其他设置。 有关设置的详细信息，请参阅下列控件描述。  
  
     你还可以使用[对话框数据交换](../mfc/dialog-data-exchange-and-validation.md)(DDX) 在一个对话框中初始化控件。  
  
5.  在对话框控件的处理程序中，使用成员变量操作控件。 有关方法的详细信息，请参阅下列控件描述。  
  
    > [!NOTE]
    >  成员变量仅当对话框本身存在时存在。 在对话框关闭后，您将无法在控件中查询输入值。 若要通过公共控件使用输入值，请重写对话框类中的 `OnOK`。 在重写中，在控件中查询输入值并将这些值存储在对话框类的成员变量中。  
  
    > [!NOTE]
    >  您还可使用对话框数据交换在对话框中设置或检索控件中的值。  
  
## <a name="remarks"></a>备注  
 向对话框添加一些公共控件将导致对话框不再工作。 请参阅[向对话框添加控件导致对话框不再函数](../windows/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md)有关处理这种情况的详细信息。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么  
  
-   [将控件添加到对话框中手动而不是使用对话框编辑器](../mfc/adding-controls-by-hand.md)  
  
-   [从标准 Windows 公共控件之一派生我的控件](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [公共控件用作子窗口](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [从控件接收通知消息](../mfc/receiving-notification-from-common-controls.md)  
  
-   [使用对话框数据交换 (DDX)](../mfc/dialog-data-exchange-and-validation.md)  
  
## <a name="see-also"></a>请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)

