---
title: "分配和取消分配窗口内存 |Microsoft 文档"
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
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 294de3c4d4ecdfcb31f6e8c227bd8a3c6764268d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-and-deallocating-window-memory"></a>分配和取消分配窗口内存
不使用 c + +**删除**运算符销毁框架窗口或视图。 而应调用`CWnd`成员函数`DestroyWindow`。 因此，应使用运算符在堆上分配框架窗口**新**。 分配的堆栈帧上或全局范围内的框架窗口时要小心。 应尽可能的堆栈帧上分配其他窗口。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [创建窗口](../mfc/creating-windows.md)  
  
-   [窗口析构序列](../mfc/window-destruction-sequence.md)  
  
-   [将 CWnd 从其 HWND 分离](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>请参阅  
 [销毁窗口对象](../mfc/destroying-window-objects.md)

