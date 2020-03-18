---
title: 将 CWnd 从其 HWND 中分离出来
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: f7a6f97ba9f1dd3a928a5450c1a899ce09a4ac5f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446956"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>将 CWnd 从其 HWND 中分离出来

如果需要规避对象`HWND` 关系，MFC 会提供另一个 `CWnd` 成员函数（即[分离](../mfc/reference/cwnd-class.md#detach)），这会断开C++窗口对象与 Windows 窗口的连接。 这会阻止析构函数在销毁对象时销毁 Windows 窗口。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [创建 windows](../mfc/creating-windows.md)

- [窗口析构序列](../mfc/window-destruction-sequence.md)

- [分配和解除分配窗口内存](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>另请参阅

[窗口对象](../mfc/window-objects.md)
