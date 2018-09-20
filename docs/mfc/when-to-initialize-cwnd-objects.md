---
title: 何时初始化 CWnd 对象 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6445190ab3da6ed84dbdd83cd0acab0ba98691f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388428"
---
# <a name="when-to-initialize-cwnd-objects"></a>何时初始化 CWnd 对象

无法创建你自己的子窗口或调用的构造函数中的任何 Windows API 函数`CWnd`-派生的对象。 这是因为`HWND`为`CWnd`尚未创建对象。 必须完成最特定于 Windows 的初始化，如添加子窗口[OnCreate](../mfc/reference/cwnd-class.md#oncreate)消息处理程序。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [创建文档框架窗口](../mfc/creating-document-frame-windows.md)

- [文档/视图创建](../mfc/document-view-creation.md)

## <a name="see-also"></a>请参阅

[使用框架窗口](../mfc/using-frame-windows.md)

