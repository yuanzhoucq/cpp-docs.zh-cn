---
title: 销毁窗口对象
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 22b483c1005931b229453ae229935c0e716ab726
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621859"
---
# <a name="destroying-window-objects"></a>销毁窗口对象

当用户完成窗口时，必须注意您自己的子窗口以销毁 c + + 窗口对象。 如果未销毁这些对象，您的应用程序将不会恢复其内存。 幸运的是，该框架管理窗口销毁以及框架窗口、视图和对话框的创建。 如果创建其他窗口，您将负责销毁它们。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [窗口销毁序列](window-destruction-sequence.md)

- [分配和取消分配窗口内存](allocating-and-deallocating-window-memory.md)

- [将 CWnd 从 HWND 中分离出来](detaching-a-cwnd-from-its-hwnd.md)

- [常用窗口创建序列](general-window-creation-sequence.md)

- [销毁框架窗口](destroying-frame-windows.md)

## <a name="see-also"></a>另请参阅

[窗口对象](window-objects.md)
