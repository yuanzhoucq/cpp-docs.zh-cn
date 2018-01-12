---
title: "框架窗口类 （体系结构） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.frame
dev_langs: C++
helpviewer_keywords: frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1caf8e4b93e18675b810ced962df6e8adcf521a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-classes-architecture"></a>框架窗口类（体系结构）
在文档/视图体系结构，框架窗口是包含视图窗口的窗口。 它们还支持具有控制条附加到它们。  
  
 多文档界面 (MDI) 应用程序，在主窗口派生自`CMDIFrameWnd`。 它间接包含文档的框架，它们是`CMDIChildWnd`对象。 `CMDIChildWnd`对象，反过来，包含文档的视图。  
  
 单文档界面 (SDI) 应用程序，在主窗口中，派生自`CFrameWnd`，包含当前文档的视图。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 SDI 应用程序的主框架窗口的基类。 此外所有其他框架窗口类的基本类。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 MDI 应用程序的主框架窗口的基类。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 MDI 应用程序的文档框架窗口的基类。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 当就地编辑时的服务器文档提供视图框架窗口。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

