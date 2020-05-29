---
title: _ATL_FUNC_INFO 结构
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: b1c740cf1a1ed344dbceb028bd1f39a87fc09363
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168587"
---
# <a name="_atl_func_info-structure"></a>_ATL_FUNC_INFO 结构

包含用于描述调度接口上的方法或属性的类型信息。

## <a name="syntax"></a>语法

```cpp
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>成员

`cc`<br/>
调用约定。 将此结构与[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)类结合使用时，必须 CC_STDCALL 此成员。 `CC_CDECL`为`CALLCONV` `_ATL_FUNC_INFO`结构的字段 Windows CE 中唯一支持的选项。 不支持任何其他值，因此其行为未定义。

`vtReturn`<br/>
函数返回值的变量类型。

`nParams`<br/>
函数参数的数目。

`pVarTypes`<br/>
函数参数的变量类型的数组。

## <a name="remarks"></a>备注

在内部，ATL 使用此结构来保存从类型库获取的信息。 如果为[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)类和[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏一起使用的事件处理程序提供类型信息，则可能需要直接操作此结构。

## <a name="example"></a>示例

给定 IDL 中定义的调度接口方法：

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

定义`_ATL_FUNC_INFO`结构：

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>要求

标头：atlcom.h

## <a name="see-also"></a>另请参阅

[类和结构](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
