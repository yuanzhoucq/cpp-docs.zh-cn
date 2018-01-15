---
title: "Windows 支持类 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.windows
dev_langs: C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 308f9deada47998c2f639d01ea5b9fdc9d04faa5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windows-support-classes"></a>Windows 支持类
下面的类提供适用于 windows 的支持：  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md)提供的包装**CreateWindow**和**CreateWindowEx**。  
  
-   [CWindow](../atl/reference/cwindow-class.md)包含用于操作窗口的方法。 `CWindow` 是 `CWindowImpl`、`CDialogImpl` 和 `CContainedWindow` 的基类。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md)实现基于新的窗口类的窗口。 此外可以子类或超类到窗口。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md)实现一个对话框。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)实现承载 ActiveX 控件的对话框 （模式或无模式）。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md)实现对话框中 （模式或无模式） 的基本功能。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md)操作承载 ActiveX 控件的窗口。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md)提供用于操作一个窗口，其中承载 ActiveX 控件，还提供的许可的 ActiveX 控件承载支持的方法。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)实现包含在另一个对象的窗口。  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的窗口类的信息。  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md)支持动态链接的消息映射。  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md)允许对象公开其消息映射到其他对象。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md)提供了标准化的 ATL 窗口对象的特征的简单方法。  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md)提供窗口样式和用于创建窗口的扩展的样式的默认值。 添加这些值，使用逻辑 OR 运算符，为在窗口的创建过程中提供的值。  
  
## <a name="related-articles"></a>相关文章  
 [ATL 窗口类](../atl/atl-window-classes.md)  
  
 [ATL 教程](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>请参阅  
 [类概述](../atl/atl-class-overview.md)   
 [消息映射宏](../atl/reference/message-map-macros-atl.md)   
 [窗口类宏](../atl/reference/window-class-macros.md)

