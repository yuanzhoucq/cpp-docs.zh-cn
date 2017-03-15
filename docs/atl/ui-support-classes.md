---
title: "UI Support Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.ui"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "用户界面, ATL 类"
  - "用户界面, support classes"
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# UI Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面选件类提供一般用户界面支持:  
  
-   [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) 对分析和呈现引擎的Microsoft HTML的接口。  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) 提供容器与控件进行通信的主方法。  管理就地控件的激活和停用。  
  
-   [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) 管理就地控件重新激活。  使无窗口控件接收消息，以及参与拖放操作。  
  
-   [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) 帮助一个就地控件与其容器之间的通信。  
  
-   [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) 使控件直接显示自身和通知容器按其显示的更改。  提供对无闪烁的绘图支持，非矩形和透明控件和命中测试。  
  
## 相关文章  
 [ATL教程](../atl/active-template-library-atl-tutorial.md)  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)