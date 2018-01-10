---
title: "不通过代码向导对控件的类型安全访问 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c5a4adce63851620326add61857433b32e1fad5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>不通过代码向导对控件进行类型安全的访问
创建对控件的类型安全访问的第一种方法是使用内联成员函数将 `CWnd` 类的 `GetDlgItem` 成员函数的返回类型转换为适当的 C++ 控件类型，如此示例中所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 然后利用类似下面这样的代码，使用此成员函数以类型安全的方式控件：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [对在对话框中的控件类型安全访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [对控件进行类型安全的访问（使用代码向导）](../mfc/type-safe-access-to-controls-with-code-wizards.md)

