---
title: 窗口对象 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 429ac52218af2e158df91c6c79f8ec67bcac3f5d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395578"
---
# <a name="window-objects"></a>窗口对象

MFC 提供类[CWnd](../mfc/reference/cwnd-class.md)封装`HWND`窗口的句柄。 `CWnd` 对象是一个 C++ 窗口对象，与表示一个 Windows 窗口但包含它的 `HWND` 不同。 使用 `CWnd` 可派生您自己的子窗口类，或使用派生自 `CWnd` 的很多 MFC 类之一。 `CWnd` 类是所有窗口的基类，包括框架窗口、对话框、子窗口、控件和控件条（如工具栏）。 更好地理解[c + + 窗口对象与 HWND 之间的关系](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)对于使用 MFC 的高效编程很重要。

MFC 提供窗口的某些默认功能和管理，但是，可以从 `CWnd` 派生您自己的类并使用其成员函数自定义所提供的功能。 您也可以构造创建子窗口`CWnd`对象并调用其[创建](../mfc/reference/cwnd-class.md#create)成员函数，然后自定义使用的子窗口`CWnd`成员函数。 您可以嵌入对象派生自[CView](../mfc/reference/cview-class.md)，例如窗体视图或树视图，框架窗口中的。 并且可以支持多个视图的拆分器窗格中，由类提供通过文档[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)。

派生自 `CWnd` 类的每个对象都包含一个消息映射，您可以通过它将 Windows 消息或命令 ID 映射到您自己的处理程序。

有关 Windows 编程的常规资料是了解如何使用可封装 `CWnd` API 的 `HWND` 成员函数的合适资源。

## <a name="functions-for-operating-on-a-cwnd"></a>用于 CWnd 的函数

`CWnd` 并将其[派生的窗口类](../mfc/derived-window-classes.md)提供构造函数、 析构函数和成员函数来初始化对象，创建基础 Windows 结构，并访问封装`HWND`。 `CWnd` 还提供了可封装 Windows API 的成员函数，以用于发送消息、访问窗口的状态、转换坐标、更新、滚动、访问剪贴板以及许多其他任务。 大多数采用 `HWND` 参数的 Windows 窗口管理 API 都封装为 `CWnd` 的成员函数。 函数的名称及其参数保留在 `CWnd` 成员函数中。 有关由封装 Windows Api 的详细信息`CWnd`，请参阅类[CWnd](../mfc/reference/cwnd-class.md)。

## <a name="cwnd-and-windows-messages"></a>CWnd 和 Windows 消息

主要用途之一`CWnd`是提供用于处理 Windows 消息，如 WM_PAINT 或 WM_MOUSEMOVE 的接口。 成员函数的许多`CWnd`是标准消息的处理程序 — 这些开头的标识符**afx_msg**和"On"前缀如`OnPaint`和`OnMouseMove`。 [消息处理和映射](../mfc/message-handling-and-mapping.md)介绍了消息和消息处理在详细信息。 这些信息同样适用于框架的窗口以及您出于特殊目的自己创建的窗口。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [C + + 窗口对象与 HWND 之间的关系](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [派生的窗口类](../mfc/derived-window-classes.md)

- [创建窗口](../mfc/creating-windows.md)

- [销毁窗口对象](../mfc/destroying-window-objects.md)

- [将 CWnd 从其 HWND 中分离出来](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [使用窗口对象](../mfc/working-with-window-objects.md)

- [设备上下文](../mfc/device-contexts.md)： 使 Windows 绘制设备独立的对象

- [图形对象](../mfc/graphic-objects.md)： 钢笔、 画笔、 字体、 位图、 调色板、 区域

## <a name="see-also"></a>请参阅

[Windows](../mfc/windows.md)

