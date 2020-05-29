---
title: OLE 控件类
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 47c28520d592c4bd49ab6cb40edbb2f5ddf59846
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447647"
---
# <a name="ole-control-classes"></a>OLE 控件类

这些是您在编写 OLE 控件时使用的主类。 OLE 控件模块中的 `COleControlModule` 类类似于应用程序中的[CWinApp](../mfc/reference/cwinapp-class.md)类。 每个模块实现一个或多个 OLE 控件；这些控件由 `COleControl` 对象表示。 这些控件使用 `CConnectionPoint` 对象与其容器进行通信。

`CPictureHolder` 和 `CFontHolder` 类封装图片和字体的 COM 接口，而 `COlePropertyPage` 和 `CPropExchange` 类可帮助您实现控件的属性页和属性存留。

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
替换 OLE 控制模块的 `CWinApp` 类。 从 `COleControlModule` 类派生来开发 OLE 控件模块对象。 它提供用于初始化 OLE 控件的模块的成员函数。

[COleControl](../mfc/reference/colecontrol-class.md)<br/>
从 `COleControl` 类派生来开发 OLE 控件。 此类从 `CWnd` 派生，它继承了 Windows 窗口对象的所有功能以及其他 OLE 特定的功能，如事件触发和支持方法和属性的功能。

[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)<br/>
`CConnectionPoint` 类定义一类用于与其他 OLE 对象进行通信的特殊接口（称为“连接点”）。 连接点可实现能够对其他对象初始化操作的传出接口，如触发事件和更改通知。

[CPictureHolder](../mfc/reference/cpictureholder-class.md)<br/>
封装 Windows 图片对象和 `IPicture` COM 接口的功能；用于实现 OLE 控件的自定义 Picture 属性。

[CFontHolder](../mfc/reference/cfontholder-class.md)<br/>
封装 Windows 字体对象和 `IFont` COM 接口的功能；用于实现 OLE 控件的堆栈 Font 属性。

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
显示图形界面（与对话框类似）中的 OLE 控件的属性。

[CPropExchange](../mfc/reference/cpropexchange-class.md)<br/>
支持 OLE 控件的属性持久性的实现。 类似于对话框的[CDataExchange](../mfc/reference/cdataexchange-class.md) 。

[CMonikerFile](../mfc/reference/cmonikerfile-class.md)<br/>
采用名字对象或可成为名字对象的字符串表示形式，并以同步方式将其绑定到名字对象为其名称的流。

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)<br/>
工作原理类似于 `CMonikerFile`；但它会以异步方式将名字对象异步绑定到名字对象为其名称的流。

[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)<br/>
实现可异步加载的 OLE 控件属性。

[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
实现异步传输并在内存文件中缓冲的 OLE 控件属性。

[COleCmdUI](../mfc/reference/colecmdui-class.md)<br/>
允许活动文档接收源自其容器的用户界面的命令（如“FileNew”、“打开”、“打印”等），并允许容器接收源自活动文档的用户界面的命令。

[COleSafeArray](../mfc/reference/colesafearray-class.md)<br/>
与任意类型和维度的数组一起使用。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
