---
title: 销毁窗口对象
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: f50d198f9868a70d25370f6c1399b66efaa5490b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297237"
---
# <a name="destroying-window-objects"></a>销毁窗口对象

必须小心使用你自己的子窗口要销毁C++当用户完成与窗口的窗口对象。 如果这些对象不会被销毁，你的应用程序将恢复其内存。 幸运的是，框架管理窗口析构，以及创建框架窗口、 视图和对话框。 如果您创建其他窗口，您有责任销毁它们。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [窗口析构序列](../mfc/window-destruction-sequence.md)

- [分配和取消分配窗口内存](../mfc/allocating-and-deallocating-window-memory.md)

- [将 CWnd 从其 HWND 中分离](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [常用窗口创建序列](../mfc/general-window-creation-sequence.md)

- [销毁框架窗口](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>请参阅

[窗口对象](../mfc/window-objects.md)
