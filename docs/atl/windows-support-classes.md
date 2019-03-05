---
title: Windows 支持类 (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.windows
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: e7e9e1f4fb94537cdd131e58ef3fc481ee1c012e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281026"
---
# <a name="windows-support-classes"></a>Windows 支持类

适用于 windows，以下类提供支持：

- [_U_MENUorID](../atl/reference/u-menuorid-class.md)提供了用于包装`CreateWindow`和`CreateWindowEx`。

- [CWindow](../atl/reference/cwindow-class.md)包含用于处理窗口的方法。 `CWindow` 是 `CWindowImpl`、`CDialogImpl` 和 `CContainedWindow` 的基类。

- [CWindowImpl](../atl/reference/cwindowimpl-class.md)实现基于新的窗口类的窗口。 此外允许您为子类或超类窗口。

- [CDialogImpl](../atl/reference/cdialogimpl-class.md)实现对话框。

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)实现承载 ActiveX 控件的对话框 （模式或无模式）。

- [CSimpleDialog](../atl/reference/csimpledialog-class.md)实现具有基本功能的对话框 （模式或无模式）。

- [CAxWindow](../atl/reference/caxwindow-class.md)操作承载 ActiveX 控件的窗口。

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md)提供用于操作的窗口，承载 ActiveX 控件并具有的许可的 ActiveX 控件承载的支持方法。

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)实现包含在另一个对象内的窗口。

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的窗口类信息。

- [CDynamicChain](../atl/reference/cdynamicchain-class.md)支持消息映射的动态链接。

- [CMessageMap](../atl/reference/cmessagemap-class.md)允许对象公开其消息映射到其他对象。

- [CWinTraits](../atl/reference/cwintraits-class.md)提供标准化的 ATL 窗口对象的特性的一个简单的方法。

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md)提供的默认值的窗口样式和用于创建窗口的扩展的样式。 使用逻辑 OR 运算符，为在窗口的创建过程中提供的值，添加这些值。

## <a name="related-articles"></a>相关文章

[ATL 窗口类](../atl/atl-window-classes.md)

[ATL 教程](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)<br/>
[消息映射宏](../atl/reference/message-map-macros-atl.md)<br/>
[窗口类宏](../atl/reference/window-class-macros.md)
