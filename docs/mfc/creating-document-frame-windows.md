---
title: 创建文档框架窗口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4b27154197e4e8347e73936f319aeb416a153d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342938"
---
# <a name="creating-document-frame-windows"></a>创建文档框架窗口
[文档/视图创建](../mfc/document-view-creation.md)演示如何[CDocTemplate](../mfc/reference/cdoctemplate-class.md)对象安排创建框架窗口、 文档和视图并将它们连接在一起。 三个[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)自变量`CDocTemplate`构造函数指定框架窗口、 文档和文档模板以响应用户命令，例如文件上的新命令动态创建的视图类菜单或 MDI 窗口菜单上的新建窗口命令。 在它创建视图和文档框架窗口时，文档模板将存储此信息以供将来使用。  
  
 有关[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)机制能够正常工作，你派生框架窗口类必须使用声明[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)宏。 这是因为框架需要以创建文档框架窗口使用类的动态构造机制`CObject`。  
  
 当用户选择命令创建一个文档时，框架会调用文档模板创建文档对象、 其视图和框架窗口将显示该视图。 文档模板创建文档框架窗口时, 创建适当的类的对象-从派生的类[CFrameWnd](../mfc/reference/cframewnd-class.md) SDI 应用程序或从[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) mdi应用程序。 框架然后调用框架窗口对象的[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)成员函数可从资源获取创建信息并创建 Windows 窗口。 框架将的窗口句柄附加到框架窗口对象。 然后，它用作子窗口的文档框架窗口创建视图。  
  
 在决定要谨慎[何时初始化](../mfc/when-to-initialize-cwnd-objects.md)你`CWnd`-派生对象。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [从 CObject （其动态创建机制） 派生类](../mfc/deriving-a-class-from-cobject.md)  
  
-   [文档/视图创建 （模板和框架窗口创建）](../mfc/document-view-creation.md)  
  
-   [销毁框架窗口](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)

