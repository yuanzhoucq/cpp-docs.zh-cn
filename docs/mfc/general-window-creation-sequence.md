---
title: 常用窗口创建序列 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3a4b67ccbba97405678985e6412cc56911bd184
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929687"
---
# <a name="general-window-creation-sequence"></a>常用窗口创建序列
在创建你自己，如子窗口的窗口时，框架将使用得多的相同的过程中所述的[文档/视图创建](../mfc/document-view-creation.md)。  
  
 MFC 为利用所提供的所有窗口类[两阶段构造](../mfc/one-stage-and-two-stage-construction-of-objects.md)。 也就是说，在 c + + 的调用期间**新**运算符，构造函数分配和初始化 c + + 对象但不会创建相应的 Windows 窗口。 通过调用完成之后[创建](../mfc/reference/cwnd-class.md#create)的窗口对象的成员函数。  
  
 `Create`成员函数才可使 Windows 窗口，并将存储其`HWND`在 c + + 对象的公共数据成员中[m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd)。 `Create` 提供的创建参数通过完整灵活性。 之前调用`Create`，你可能想要的窗口类注册为全局函数[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)若要设置帧的图标和类样式。  
  
 对于框架窗口，你可以使用[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)成员函数而不是`Create`。 `LoadFrame` 使 Windows 窗口使用较少的参数。 它会从资源，包括帧的标题、 图标、 快捷键对应表和菜单获取多个默认值。  
  
> [!NOTE]
>  图标、 快捷键对应表和菜单资源必须具有一个公共的资源 ID，如**IDR_MAINFRAME**，它们由 LoadFrame 加载。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [窗口对象](../mfc/window-objects.md)  
  
-   [注册窗口"类"](../mfc/registering-window-classes.md)  
  
-   [销毁窗口对象](../mfc/destroying-window-objects.md)  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>请参阅  
 [创建窗口](../mfc/creating-windows.md)

