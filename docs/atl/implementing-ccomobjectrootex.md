---
title: "Implementing CComObjectRootEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CComObjectRootEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectRoot class, 实现"
  - "CComObjectRootEx class"
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Implementing CComObjectRootEx
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 非常重要；所有 ATL 对象必须在其继承中有一个 `CComObjectRootEx` 或 [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 的实例。  `CComObjectRootEx` 提供基于 COM 映射项的默认 `QueryInterface` 机制。  
  
 通过其 COM 映射，对象的接口将在客户端查询接口时向该客户端公开。  该查询通过 `CComObjectRootEx::InternalQueryInterface` 执行。  `InternalQueryInterface` 仅处理 COM 映射表中的接口。  
  
 你可以使用 [COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20\(ATL\).md) 宏或它的一个变体将接口输入到 COM 映射表。  例如，以下代码输入可将接口 `IDispatch`、`IBeeper` 和 `ISupportErrorInfo` 输入到 COM 映射表：  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/CPP/implementing-ccomobjectrootex_1.h)]  
  
## 请参阅  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [COM Map Macros](../atl/reference/com-map-macros.md)