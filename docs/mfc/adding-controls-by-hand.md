---
title: "将控件手动添加 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b13f6fdfb3c11819eb8d8838e5617e7a349d1023
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-by-hand"></a>手动添加控件
你可以[将控件添加到对话框中，使用对话框编辑器](../mfc/using-the-dialog-editor-to-add-controls.md)或将它们添加你自己，用代码。  
  
 若要创建自己的控件对象，通常将嵌入在 c + + 对话框中的 c + + 控件对象或框架窗口对象。 类似于 framework 中的许多其他对象，控件需要两阶段构造。 你应调用控件的**创建**作为创建父对话框或框架窗口的一部分的成员函数。 对于对话框，这通常是[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，和框架窗口中[OnCreate](../mfc/reference/cwnd-class.md#oncreate)。  
  
 下面的示例演示如何可能会声明`CEdit`对象派生的对话框类的类声明中，然后调用**创建**成员函数在`OnInitDialog`。 因为`CEdit`对象声明为嵌入的对象，它将自动构造对话框对象构造的但仍必须有其自己初始化时**创建**成员函数。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]  
  
 以下`OnInitDialog`函数将设置一个矩形，然后调用**创建**创建 Windows 编辑控件并将其附加到未初始化`CEdit`对象。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]  
  
 创建编辑对象后，你还可以设置输入的焦点控制通过调用`SetFocus`成员函数。 最后，返回从 0`OnInitDialog`以显示将焦点设置。 如果返回一个非零值时，对话框管理器将焦点设置到对话框项列表中的第一个控件项。 在大多数情况下，你将想要将控件添加到你的对话框中，使用对话框编辑器。  
  
## <a name="see-also"></a>请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

