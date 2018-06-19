---
title: 将 CWnd 从其 HWND 中分离 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a776b4ff4799750c89a322379a063030db748eec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342674"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>将 CWnd 从其 HWND 中分离出来
如果想要绕过的对象-`HWND`关系，MFC 提供了另一个`CWnd`成员函数，[分离](../mfc/reference/cwnd-class.md#detach)，这与 Windows 窗口断开连接的 c + + 窗口对象。 这可以防止析构函数时销毁该对象将销毁 Windows 窗口。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [创建窗口](../mfc/creating-windows.md)  
  
-   [窗口析构序列](../mfc/window-destruction-sequence.md)  
  
-   [分配和取消分配窗口内存](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>请参阅  
 [窗口对象](../mfc/window-objects.md)

