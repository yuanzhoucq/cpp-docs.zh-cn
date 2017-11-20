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
ms.openlocfilehash: 3d1f0635933d2cf27b824c8b0a93f66429e22ea8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>将 CWnd 从其 HWND 中分离出来
如果想要绕过的对象-`HWND`关系，MFC 提供了另一个`CWnd`成员函数，[分离](../mfc/reference/cwnd-class.md#detach)，这与 Windows 窗口断开连接的 c + + 窗口对象。 这可以防止析构函数时销毁该对象将销毁 Windows 窗口。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [创建窗口](../mfc/creating-windows.md)  
  
-   [窗口析构序列](../mfc/window-destruction-sequence.md)  
  
-   [分配和取消分配窗口内存](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>另请参阅  
 [窗口对象](../mfc/window-objects.md)

