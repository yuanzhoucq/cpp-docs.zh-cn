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
ms.openlocfilehash: 33d471b41c8f1fd670e25626049ecd9b06b034e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195195"
---
# <a name="allocating-and-deallocating-window-memory"></a>分配和取消分配窗口内存

不要使用 c + + **`delete`** 运算符销毁框架窗口或视图。 请改为调用 `CWnd` 成员函数 `DestroyWindow` 。 因此，应在带有运算符的堆上分配框架窗口 **`new`** 。 在堆栈帧上或全局分配框架窗口时请小心。 应尽可能在堆栈帧上分配其他窗口。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [创建窗口](creating-windows.md)

- [窗口销毁序列](window-destruction-sequence.md)

- [将 CWnd 从 HWND 中分离出来](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>另请参阅

[销毁窗口对象](destroying-window-objects.md)
