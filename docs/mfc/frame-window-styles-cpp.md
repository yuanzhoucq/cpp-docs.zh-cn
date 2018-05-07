---
title: 框架窗口样式 （c + +） |Microsoft 文档
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
ms.openlocfilehash: 102b3a4c8372a53aada23ad448ce5dc1cf323a97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="frame-window-styles-c"></a>框架窗口样式 (C++)
获取与框架的框架窗口适用于大多数程序，但你可以通过使用高级的函数来获得更大的灵活性[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)和 MFC 全局函数[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` 是的成员函数`CWnd`。  
  
 如果将应用**WS_HSCROLL**和**WS_VSCROLL**到主框架窗口的样式，它们而是应用于**MDICLIENT**窗口，以便用户可以滚动**MDICLIENT**区域。  
  
 如果窗口的**FWS_ADDTOTITLE**样式位设置 （即它默认情况下），视图表明框架窗口要根据视图的文档名称的窗口的标题栏中显示的标题。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [管理 MDI 子窗口 (MDICLIENT)](../mfc/managing-mdi-child-windows.md)中包含的 MDI 子窗口的 MDI 框架, 窗口  
  
-   [更改 mfc 创建的窗口样式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [窗口样式](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>请参阅  
 [框架窗口](../mfc/frame-windows.md)

