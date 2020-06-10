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
ms.openlocfilehash: e15a2a6bc016bf23bc0decf529b4c3ffeecc3a4c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621950"
---
# <a name="creating-document-frame-windows"></a>创建文档框架窗口

[文档/视图创建](document-view-creation.md)显示了[CDocTemplate](reference/cdoctemplate-class.md)对象如何协调创建框架窗口、文档和视图，以及如何将它们连接在一起。 构造函数的三个[CRuntimeClass](reference/cruntimeclass-structure.md)参数 `CDocTemplate` 指定框架窗口、文档和视图类，文档模板会动态创建这些类以响应用户命令，例如 "文件" 菜单上的 "新建" 命令或 MDI 窗口菜单上的 "新建窗口" 命令。 文档模板存储此信息以供以后在为视图和文档创建框架窗口时使用。

为了使[RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class)机制正常工作，必须使用[DECLARE_DYNCREATE](reference/run-time-object-model-services.md#declare_dyncreate)宏声明派生的框架窗口类。 这是因为框架需要使用类的动态构造机制来创建文档框架窗口 `CObject` 。

当用户选择创建文档的命令时，框架会在文档模板上调用以创建文档对象、其视图和将显示该视图的框架窗口。 当它创建文档框架窗口时，文档模板会创建一个适当类的对象，该对象是从 SDI 应用程序的[CFrameWnd](reference/cframewnd-class.md)派生的类，或者为 MDI 应用程序的[CMDIChildWnd](reference/cmdichildwnd-class.md) 。 然后，框架将调用框架窗口对象的[LoadFrame](reference/cframewnd-class.md#loadframe)成员函数，以从资源中获取创建信息并创建 Windows 窗口。 框架将窗口句柄附加到框架窗口对象。 然后创建该视图作为文档框架窗口的子窗口。

在确定[何时初始化](when-to-initialize-cwnd-objects.md)派生对象时，请务必小心 `CWnd` 。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [从 CObject 派生类（其动态创建机制）](deriving-a-class-from-cobject.md)

- [文档/视图创建（模板和框架窗口创建）](document-view-creation.md)

- [销毁框架窗口](destroying-frame-windows.md)

## <a name="see-also"></a>另请参阅

[使用框架窗口](using-frame-windows.md)
