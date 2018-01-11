---
title: "将 CWnd 从其 HWND 中分离 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWnd
dev_langs: C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6aa24e0e9a0d9ee50a0c5c69e280ea7a727ca38b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>将 CWnd 从其 HWND 中分离出来
如果想要绕过的对象-`HWND`关系，MFC 提供了另一个`CWnd`成员函数，[分离](../mfc/reference/cwnd-class.md#detach)，这与 Windows 窗口断开连接的 c + + 窗口对象。 这可以防止析构函数时销毁该对象将销毁 Windows 窗口。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [创建窗口](../mfc/creating-windows.md)  
  
-   [窗口析构序列](../mfc/window-destruction-sequence.md)  
  
-   [分配和取消分配窗口内存](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>请参阅  
 [窗口对象](../mfc/window-objects.md)

