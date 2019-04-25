---
title: 创建文档框架窗口
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: 66a951994a75cbd99debeb2c6511739411cdd470
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174024"
---
# <a name="creating-document-frame-windows"></a>创建文档框架窗口

[文档/视图创建](../mfc/document-view-creation.md)显示了如何[CDocTemplate](../mfc/reference/cdoctemplate-class.md)对象会协调创建框架窗口、 文档和视图，并将它们连接起来。 三个[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)自变量`CDocTemplate`构造函数指定框架窗口、 文档和文档模板以响应用户命令，如新建命令对该文件可动态创建的视图类菜单或 MDI 窗口菜单上的新建窗口命令。 创建视图和文档框架窗口时，文档模板将存储此信息以供将来使用。

有关[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)机制能够正常运行，将派生框架窗口类必须使用声明[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)宏。 这是因为框架需要创建文档框架窗口使用类的动态构造机制`CObject`。

当用户选择的命令，创建一个文档时，框架将调用文档模板创建文档对象、 其视图和框架窗口将显示在视图中。 如果创建文档框架窗口时，文档模板会创建相应的类的对象 — 类派生自[CFrameWnd](../mfc/reference/cframewnd-class.md) SDI 应用程序或从[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)为 MDI应用程序。 然后，framework 调用框架窗口对象的[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)成员函数从资源获取创建信息并创建 Windows 窗口。 该框架将窗口句柄附加到框架窗口对象。 然后它将作为子窗口的文档框架窗口创建视图。

在决定要小心[何时初始化](../mfc/when-to-initialize-cwnd-objects.md)你`CWnd`-派生的对象。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [从 CObject （其动态创建机制） 派生一个类](../mfc/deriving-a-class-from-cobject.md)

- [文档/视图创建 （模板和框架窗口创建）](../mfc/document-view-creation.md)

- [销毁框架窗口](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>请参阅

[使用框架窗口](../mfc/using-frame-windows.md)
