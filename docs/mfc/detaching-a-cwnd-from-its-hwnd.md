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
ms.openlocfilehash: 2e0484698654cd14f22a92be76a80f71c0f9adf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621848"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>将 CWnd 从其 HWND 中分离出来

如果需要规避对象 `HWND` 关系，MFC 将提供另一个 `CWnd` 成员函数（即[分离](reference/cwnd-class.md#detach)），这会断开 c + + 窗口对象与 Windows 窗口的连接。 这会阻止析构函数在销毁对象时销毁 Windows 窗口。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [创建 windows](creating-windows.md)

- [窗口销毁序列](window-destruction-sequence.md)

- [分配和取消分配窗口内存](allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>另请参阅

[窗口对象](window-objects.md)
