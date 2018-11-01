---
title: 分配和取消分配窗口内存
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: a9bbf92a586a910dfa4e81774ce4817c9cf458e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582489"
---
# <a name="allocating-and-deallocating-window-memory"></a>分配和取消分配窗口内存

不使用 c + +**删除**运算符来销毁框架窗口或视图。 改为调用`CWnd`成员函数`DestroyWindow`。 因此，应使用运算符在堆上分配框架窗口**新**。 分配堆栈帧上或全局范围内的框架窗口时要小心。 应尽可能的堆栈帧上分配其他窗口。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [创建窗口](../mfc/creating-windows.md)

- [窗口析构序列](../mfc/window-destruction-sequence.md)

- [将 CWnd 从其 HWND 中分离](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>请参阅

[销毁窗口对象](../mfc/destroying-window-objects.md)

