---
title: ATL 窗口类简介 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbd433eb024e7715c065a005ce06d38a086a5072
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765479"
---
# <a name="introduction-to-atl-window-classes"></a>ATL 窗口类简介

下面的 ATL 类可实现和操作窗口：

- [CWindow](../atl/reference/cwindow-class.md)允许您附加的窗口句柄`CWindow`对象。 然后，调用`CWindow`操作窗口的方法。

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) ，可实现新的窗口和处理消息映射的消息。 您可以创建基于新的 Windows 类、 超类现有类或子类现有窗口窗口。

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) ，可实现在安装结束时或使用消息映射无模式对话框框和处理消息。

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)是一个预生成的类，另一个类中实现其消息映射包含一个窗口。 使用`CContainedWindowT`允许您集中在一个类中的消息处理。

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)功能可以实现承载 ActiveX 控件的对话框 （模式或无模式）。

- [CSimpleDialog](../atl/reference/csimpledialog-class.md)功能可以实现具有基本功能的模式对话框。

- [CAxWindow](../atl/reference/caxwindow-class.md)功能可以实现承载 ActiveX 控件的窗口。

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md)功能可以实现承载授权的 ActiveX 控件的窗口。

除了特定的窗口类，ATL 提供了几个类旨在简化 ATL 窗口对象的实现。 它们是：

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的窗口类信息。

- [CWinTraits](../atl/reference/cwintraits-class.md)并[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)提供标准化的 ATL 窗口对象的特性的一个简单的方法。

## <a name="see-also"></a>请参阅

[窗口类](../atl/atl-window-classes.md)

