---
title: "_ATL_FUNC_INFO 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 7bc607931c486f3dd7a398b277048db77e9b2f62
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO 结构
包含用于描述在调度接口上的方法或属性的类型信息。  
  
## <a name="syntax"></a>语法  
  
```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```  
  
## <a name="members"></a>成员  
 **抄送**  
 调用约定。 使用此结构与时[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)类，此成员必须是**CC_STDCALL**。 `CC_CDECL`是在 Windows CE 中受支持的唯一选项`CALLCONV`字段`_ATL_FUNC_INFO`结构。 任何其他值不受支持因此其行为未定义。  
  
 **vtReturn**  
 变体类型的函数返回值。  
  
 **nParams**  
 函数参数的数目。  
  
 **pVarTypes**  
 变体类型的函数参数的数组。  
  
## <a name="remarks"></a>备注  
 在内部，ATL 还使用此结构来保存获取从类型库的信息。 你可能需要直接操作此结构，如果你提供用于对事件处理程序的类型信息[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)类和[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏。  
  
## <a name="example"></a>示例  
 给定 IDL 中定义的调度接口方法︰  
  
 [!code-cpp[NVC_ATL_Windowing # 139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 您应该定义`_ATL_FUNC_INFO`结构︰  
  
 [!code-cpp[NVC_ATL_Windowing # 140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
## <a name="see-also"></a>另请参阅  
 [结构](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)






