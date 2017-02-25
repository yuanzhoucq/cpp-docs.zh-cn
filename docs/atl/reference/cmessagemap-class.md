---
title: "CMessageMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMessageMap"
  - "ATL.CMessageMap"
  - "ATL::CMessageMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 消息处理程序"
  - "CMessageMap class"
  - "message maps, ATL"
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMessageMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类允许对象的消息映射是访问由另一个对象。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class ATL_NO_VTABLE CMessageMap  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMessageMap::ProcessWindowMessage](../Topic/CMessageMap::ProcessWindowMessage.md)|访问 `CMessageMap`的消息映射派生类。|  
  
## 备注  
 `CMessageMap` 是允许对象的消息映射被其他对象获取的抽象基类。  为了对象可以显示其消息映射，其选件类必须从 `CMessageMap`派生。  
  
 ATL使用 `CMessageMap` 支持包含窗口和动态消息映射绑定。  例如，包含 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 对象的任何选件类必须从 `CMessageMap`派生。  下面的代码从 [SUBEDIT](../../top/visual-cpp-samples.md) 示例中采用。  通过 [CComControl](../../atl/reference/ccomcontrol-class.md)，`CAtlEdit` 选件类从 `CMessageMap`自动派生。  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/CPP/cmessagemap-class_1.h)]  
  
 由于包含窗口，`m_EditCtrl`，在包含的选件类将使用消息映射，`CAtlEdit` 从 `CMessageMap`派生。  
  
 有关消息映射的更多信息，请参见 [消息映射](../../atl/message-maps-atl.md) 在该文章“ATL窗口选件类上”。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [CDynamicChain Class](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)