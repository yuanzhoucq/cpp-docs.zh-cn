---
title: "使用热键控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0a64de06d5bc499d5b566d6d40508d08e920264
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-hot-key-control"></a>使用热键控件
热键控件的典型用法遵循以下模式：  
  
-   创建滑块控件。 如果滑块控件是在对话框模板中指定的，则在创建对话框时自动进行创建。 (你应具有[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)对应于热键控件的对话框类中的成员。)或者，可以使用[创建](../mfc/reference/chotkeyctrl-class.md#create)成员函数来创建控件用作子窗口的任何窗口。  
  
-   如果你想要设置控件的默认值，调用[SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey)成员函数。 如果你想要禁止某些 shift 状态，调用[设置规则](../mfc/reference/chotkeyctrl-class.md#setrules)。 有关控件在对话框中，执行此操作的好时机是在对话框中的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数。  
  
-   用户与该控件交互热键控件具有焦点时，按热键组合。 用户然后以某种方式指示此任务已完成，可能是通过单击对话框中的按钮。  
  
-   当用户已选定热键向程序通知时，它应使用成员函数[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)从热键控件中检索虚拟键和 shift 状态值。  
  
-   一旦您知道什么密钥选定的用户，就可以设置热键使用中所述的方法之一[设置热键](../mfc/setting-a-hot-key.md)。  
  
-   热键控件是否在对话框中，它与`CHotKeyCtrl`将自动销毁对象。 否则，您需要确保正确地销毁控件和 `CHotKeyCtrl` 对象。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)

