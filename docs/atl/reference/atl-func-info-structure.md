---
title: "_ATL_FUNC_INFO Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_FUNC_INFO"
  - "ATL::_ATL_FUNC_INFO"
  - "ATL._ATL_FUNC_INFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_FUNC_INFO structure"
  - "ATL_FUNC_INFO structure"
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# _ATL_FUNC_INFO Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含类型用于的信息描述一个方法或属性在调度接口。  
  
## 语法  
  
```  
  
      struct _ATL_FUNC_INFO{  
   CALLCONV cc;  
   VARTYPE vtReturn;  
   SHORT nParams;  
   VARTYPE pVarTypes[_ATL_MAX_VARTYPES];  
};  
```  
  
## 成员  
 **cc**  
 调用约定。  当使用 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 选件类时的此结构，此成员必须是 **CC\_STDCALL**。  `CC_CDECL` 是在 `_ATL_FUNC_INFO` 结构的 `CALLCONV` 字段的Windows CE支持的唯一选项。  其他值因此不受支持其未定义的行为。  
  
 **vtReturn**  
 函数的不同类型的返回值。  
  
 **nParams**  
 函数参数的数目。  
  
 **pVarTypes**  
 一组功能参数具有不同的类型。  
  
## 备注  
 在内部，ATL使用此机制。信息负从类型库中获取的。  如果您为事件处理程序提供类型信息用于 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 选件类和 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md) 宏，您可能需要直接操作该结构。  
  
## 示例  
 将在IDL中定义的调度接口方法:  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/CPP/atl-func-info-structure_1.idl)]  
  
 您应定义一 `_ATL_FUNC_INFO` 结构:  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/CPP/atl-func-info-structure_2.h)]  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [结构](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl Class](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)