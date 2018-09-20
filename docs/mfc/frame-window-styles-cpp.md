---
title: 框架窗口样式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f0e4bde874fc563535b661108cb68edefd8d977
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385009"
---
# <a name="frame-window-styles-c"></a>框架窗口样式 (C++)

获取与框架的框架窗口是适用于大多数程序中，但可以通过使用高级的函数来获得更大的灵活性[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) MFC 全局函数和[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` 是的成员函数`CWnd`。

如果将应用**WS_HSCROLL**并**WS_VSCROLL**到主框架窗口样式，而是对应用这些**MDICLIENT**窗口，使用户可以滚动浏览**MDICLIENT**区域。

如果在窗口**FWS_ADDTOTITLE**样式位设置 （这是默认情况下），则视图将通知框架窗口根据视图的文档名称的窗口的标题栏中显示哪些标题。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [管理 MDI 子窗口 (MDICLIENT)](../mfc/managing-mdi-child-windows.md)内包含 MDI 子窗口的 MDI 框架, 窗口

- [更改 MFC 创建的窗口样式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [窗口样式](../mfc/reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>请参阅

[框架窗口](../mfc/frame-windows.md)

