---
title: 从对话框对象检索数据 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ac243333c8dc778486dd18323658f262c6d6610
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380203"
---
# <a name="retrieving-data-from-the-dialog-object"></a>从对话框对象检索数据
框架可以轻松地进行初始化的控件在对话框中的值并从控件中检索值。 更费力的手动方法是调用函数，如`SetDlgItemText`和`GetDlgItemText`类的成员函数`CWnd`，其应用到控制窗口。 使用这些函数中，你访问每个控件单独来设置或获取其值，如调用函数`SetWindowText`和`GetWindowText`。 初始化和检索，自动执行框架的方法。  
  
 对话框数据交换 (DDX) 可以更轻松地交换的控件中的对话框对象中的对话框框和成员变量之间的数据。 此 exchange 两种方式工作。 若要初始化的控件在对话框中，你可以在对话框对象中设置数据成员的值和框架将这些值传输给控件之前显示的对话框。 然后你可以随时更新对话框数据成员与用户输入的数据。 此时，你可以使用通过引用数据成员变量的数据。  
  
 你还可以安排对话框控件以使用对话框数据验证 (DDV) 来自动验证的值。  
  
 中的更详细地解释了 DDX 和 DDV[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。  
  
 对于模式对话框，你可以检索用户输入时的任何数据`DoModal`返回**IDOK**但对话框之前在销毁对象。 对于无模式对话框，你可以从检索数据的对话框对象在任何时候通过调用`UpdateData`具有自变量**TRUE** ，然后访问对话框类成员变量。 中的更详细地讨论了此主题[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。  
  
## <a name="see-also"></a>请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

