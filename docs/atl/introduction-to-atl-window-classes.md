---
title: ATL 窗口类简介 |Microsoft 文档
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
ms.openlocfilehash: ea9b275831aee3ea96da1036019db07f9e2dfc93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-atl-window-classes"></a>ATL 窗口类简介
下面的 ATL 类旨在实现和操作窗口：  
  
-   [CWindow](../atl/reference/cwindow-class.md)使您可以连接到的窗口句柄`CWindow`对象。 然后，你调用`CWindow`操作窗口的方法。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md)允许你可以实现新的窗口和处理消息映射的消息。 你可以创建基于新 Windows 类、 超类现有类或子类现有的窗口的窗口。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md)让你能够实现在安装结束时或使用消息映射无模式对话框框和处理消息。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)是另一个类中实现包含其消息映射的窗口的预构建的类。 使用`CContainedWindowT`允许您集中某个类中的消息处理。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)让你能够实现承载 ActiveX 控件的对话框 （模式或无模式）。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md)让你能够实现具有基本功能的模式对话框。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md)让你能够实现承载 ActiveX 控件的窗口。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md)让你能够实现承载授权的 ActiveX 控件的窗口。  
  
 除了特定窗口类，ATL 提供多个类旨在简化 ATL 窗口对象的实现。 它们是：  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的窗口类的信息。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md)和[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)提供标准化 ATL 窗口对象的特征的简单方法。  
  
## <a name="see-also"></a>请参阅  
 [窗口类](../atl/atl-window-classes.md)

