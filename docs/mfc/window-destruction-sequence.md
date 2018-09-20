---
title: 窗口析构序列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04ef1aa9dadbbe965ab17945da681a0e1189c404
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446631"
---
# <a name="window-destruction-sequence"></a>窗口析构序列

在 MFC 框架中，当用户关闭帧窗口时，窗口的默认[OnClose](../mfc/reference/cwnd-class.md#onclose)处理程序调用[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)。 当销毁 Windows 窗口时调用的最后一个成员函数是[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)，其中进行一些清理，调用[默认](../mfc/reference/cwnd-class.md#default)成员函数来执行 Windows 清理，最后调用虚拟成员函数[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)。 [CFrameWnd](../mfc/reference/cframewnd-class.md)的实现`PostNcDestroy`删除 c + + 窗口对象。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [分配和取消分配窗口内存](../mfc/allocating-and-deallocating-window-memory.md)

- [将 CWnd 从其 HWND 中分离](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>请参阅

[销毁窗口对象](../mfc/destroying-window-objects.md)

