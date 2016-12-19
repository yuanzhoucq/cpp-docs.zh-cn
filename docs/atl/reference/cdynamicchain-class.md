---
title: "CDynamicChain Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CDynamicChain"
  - "ATL.CDynamicChain"
  - "CDynamicChain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicChain class"
  - "chaining message maps"
  - "message maps, 链接"
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicChain Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供支持动态绑定消息映射的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CDynamicChain  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDynamicChain::CDynamicChain](../Topic/CDynamicChain::CDynamicChain.md)|构造函数。|  
|[CDynamicChain::~CDynamicChain](../Topic/CDynamicChain::~CDynamicChain.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDynamicChain::CallChain](../Topic/CDynamicChain::CallChain.md)|处理一Windows消息传送到另一个对象的消息映射。|  
|[CDynamicChain::RemoveChainEntry](../Topic/CDynamicChain::RemoveChainEntry.md)|从集合中移除消息映射项。|  
|[CDynamicChain::SetChainEntry](../Topic/CDynamicChain::SetChainEntry.md)|添加消息映射项添加到集合或修改现有项。|  
  
## 备注  
 `CDynamicChain` 管理消息映射的集合，使Windows消息处理，在运行时，到另一个对象的消息映射。  
  
 若要添加对动态绑定消息映射，请执行以下操作:  
  
-   从 `CDynamicChain`派生您的选件类。  在消息映射，请指定 [CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md) 宏绑定到另一个对象的默认消息映射。  
  
-   派生要绑定到从 [CMessageMap](../../atl/reference/cmessagemap-class.md)的每选件类。  `CMessageMap` 允许对象显示其消息映射在其他对象。  
  
-   调用对象，并显示消息映射要绑定的 `CDynamicChain::SetChainEntry` 标识。  
  
 例如，假定您的选件类定义如下:  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/CPP/cdynamicchain-class_1.h)]  
  
 客户端然后调用 `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/CPP/cdynamicchain-class_2.cpp)]  
  
 其中 `chainedObj` 所绑定到的对象是从 `CMessageMap`派生的选件类的实例。  现在，因此，如果 `myCtl` 接收不受 `OnPaint` 或 `OnSetFocus`处理的消息，窗口过程处理消息。`chainedObj`的默认消息映射。  
  
 有关绑定的消息映射的更多信息，请参见 [消息映射](../../atl/message-maps-atl.md) 在该文章“ATL窗口选件类上”。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)