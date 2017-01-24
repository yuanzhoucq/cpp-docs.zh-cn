---
title: "Controls: General Support Classes | Microsoft Docs"
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
  - "vc.atl.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件 [ATL]"
  - "general support classes"
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controls: General Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面选件类提供常规为ATL控件支持的:  
  
-   [CComControl](../atl/reference/ccomcontrol-class.md) 包括帮助器为ATL控件至关重要的函数和数据成员。  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) 提供方法所需的控件。  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) 提供容器与控件进行通信的主方法。  管理就地控件的激活和停用。  
  
-   [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) 将初始化为一个调用帮助容器避免延迟，在加载控件。  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) 为一个否则非活动控件提供最小鼠标交互。  
  
## 示例程序  
 [ATLFire](../top/visual-cpp-samples.md)  
  
## 相关文章  
 [ATL教程](../atl/active-template-library-atl-tutorial.md)  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)