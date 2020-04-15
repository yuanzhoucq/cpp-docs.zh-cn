---
title: 空闲循环处理
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
ms.openlocfilehash: 9579d4bb8768b0227453af401d6fdc8a8bd482b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376013"
---
# <a name="idle-loop-processing"></a>空闲循环处理

很多应用程序“在后台”执行长时间的处理。 有时候，出于性能考虑，不得不对此类工作使用多线程处理。 线程涉及额外的开发开销，因此不建议它们执行简单任务，如 MFC 在[OnIdle](../mfc/reference/cwinthread-class.md#onidle)函数中所做的空闲时间工作。 本文将重点介绍空闲处理。 有关多线程的详细信息，请参阅[多线程主题](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

某些类型的后台处理会在用户未以其他方式与应用程序交互的时间间隔内适当地完成。 在为 Microsoft Windows 操作系统开发的应用程序中，应用程序可通过将漫长的过程拆分为很多小片段来执行空闲处理。 处理每个片段后，应用程序使用[PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew)循环向 Windows 生成执行控制。

本文将介绍两种在应用程序中执行空闲处理的方法：

- 在 MFC 的主消息循环中使用**PeekMessage。**

- 在应用程序中的其他地方嵌入另一个**PeekMessage**循环。

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>在 MFC 消息循环中窥视消息

在使用 MFC 开发的应用程序中，`CWinThread`类中的主消息循环包含一个消息循环，该消息循环称为[PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) Win32 API。 此循环也称为消息之间的 `OnIdle` 的 `CWinThread` 成员函数。 应用程序可通过重写 `OnIdle` 函数处理此空闲时间中的消息。

> [!NOTE]
> `Run``OnIdle`，和某些其他成员函数现在是类`CWinThread`的成员，而不是类`CWinApp`的成员。 `CWinApp` 派生自 `CWinThread`。

有关执行空闲处理的详细信息，请参阅*MFC 参考*中的[OnIdle。](../mfc/reference/cwinthread-class.md#onidle)

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>在应用程序中的其他地方窥视消息

在应用程序中执行空闲处理的另一个方法涉及在您的其中一个函数中嵌入消息循环。 此消息循环与 MFC 的主消息循环非常相似，该循环位于[CWinThread：：run](../mfc/reference/cwinthread-class.md#run)中。 这意味着使用 MFC 开发的应用程序中的此类循环必须执行很多与主消息循环相同的函数。 以下代码片段演示了编写与 MFC 兼容的消息循环：

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

只要有要执行的空闲处理，嵌入函数中的此代码就会循环。 在该循环中，嵌套循环重复调用`PeekMessage`。 只要该调用返回非零值，该循环就会调用 `CWinThread::PumpMessage` 以执行常规消息转换和调度。 尽管没有 `PumpMessage` 的文档说明，但可以在 Visual C++ 安装的 \atlmfc\src\mfc 目录的 ThrdCore.Cpp 文件中检查其源代码。

内部循环结束后，外部循环将通过对 `OnIdle` 进行一次或多次调用执行空闲处理。 第一次调用是针对 MFC 的。 您可以对 `OnIdle` 进行更多调用以完成自己的后台工作。

有关执行空闲处理的详细信息，请参阅 MFC 库参考中的[OnIdle。](../mfc/reference/cwinthread-class.md#onidle)

## <a name="see-also"></a>另请参阅

[一般 MFC 主题](../mfc/general-mfc-topics.md)
