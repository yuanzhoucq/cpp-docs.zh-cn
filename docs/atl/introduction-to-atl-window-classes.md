---
title: "Introduction to ATL Window Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "window classes"
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Introduction to ATL Window Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的ATL选件类旨在实现和操作窗口:  
  
-   [CWindow](../atl/reference/cwindow-class.md) 可以附加窗口句柄 `CWindow` 对象。  然后调用 `CWindow` 方法操作窗口。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) 可以实现一个新窗口，并处理消息的消息映射以。  可以创建基于新的Windows选件类、创建超类时现有选件类或子类的窗口现有的窗口。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) 可以实现模式或无模式对话框和处理消息的消息映射。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) 是实现一个窗口消息映射在另一选件类包含预生成的选件类。  使用 `CContainedWindowT` 使您能够集中精力处理在一选件类的消息。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) 可以实现对话框\(模式或无模式\)承载ActiveX控件。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) 可以实现具有基本功能的模式对话框。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) 可以实现一个承载ActiveX控件的窗口。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) 可以实现承载一个授权的ActiveX控件的窗口。  
  
 除了特定窗口选件类之外，ATL提供了模型中的多个选件类使实现ATL窗口创建更容易。  具体如下：  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 管理新的windows选件类的信息。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) 和 [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) 提供标准化ATL窗口对象的特征一种简单的方法。  
  
## 请参阅  
 [窗口类](../atl/atl-window-classes.md)