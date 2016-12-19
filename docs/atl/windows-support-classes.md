---
title: "Windows Support Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.windows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 窗口"
  - "windows [C++], ATL"
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面选件类提供对window的支持:  
  
-   [\_U\_MENUorID](../atl/reference/u-menuorid-class.md) 为 **CreateWindow** 和 **CreateWindowEx**提供包装。  
  
-   [CWindow](../atl/reference/cwindow-class.md) 包含操作的windows方法。  `CWindow` 是 `CWindowImpl`、`CDialogImpl` 和 `CContainedWindow` 的基类。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) 实现基于新的windows选件类的窗口。  并允许您对子类或创建超类时窗口。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) 实现一个对话框。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) 实现一个对话框\(模式或无模式\)承载ActiveX控件。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) 实现一个对话框\(模式或无模式\)具有基本功能。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) 操作承载一个ActiveX控件的窗口。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) 用于操作承载一个ActiveX控件并为承载授权的ActiveX控件支持的windows提供方法。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) 实现在其他对象中包含的窗口。  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 管理新的windows选件类的信息。  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md) 支持动态绑定消息映射。  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) 允许对象显示其消息映射在其他对象。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) 提供标准化ATL窗口对象的特征一种简单的方法。  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) 提供用于的窗口样式和扩展样式提供默认创建一个窗口。  使用逻辑或运算符，这些值将添加，窗口中的创建时提供的值。  
  
## 相关文章  
 [ATL窗口选件类](../atl/atl-window-classes.md)  
  
 [ATL教程](../atl/active-template-library-atl-tutorial.md)  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)   
 [Message Map Macros](../atl/reference/message-map-macros-atl.md)   
 [Window Class Macros](../atl/reference/window-class-macros.md)