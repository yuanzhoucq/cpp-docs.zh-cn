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
ms.openlocfilehash: f6cf32bab86d741f3b0750c150c7bbc647b27ddc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299538"
---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO 结构

包含用于描述调度接口方法或属性的类型信息。

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

`cc`<br/>
调用约定。 使用此结构与时[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)类，此成员必须为 CC_STDCALL。 `CC_CDECL` 是在 Windows CE 中支持的唯一选项`CALLCONV`字段的`_ATL_FUNC_INFO`结构。 任何其他值不受支持因此其行为未定义。

`vtReturn`<br/>
该函数的变体类型返回值。

`nParams`<br/>
函数参数的数目。

`pVarTypes`<br/>
函数参数的 variant 类型的数组。

## <a name="remarks"></a>备注

在内部，ATL 还使用此结构来保存从类型库获取的信息。 可能需要直接操作此结构，如果您提供事件处理程序与一起使用的类型信息[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)类和[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏。

## <a name="example"></a>示例

给定 IDL 中定义的调度接口方法：

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

您需要定义`_ATL_FUNC_INFO`结构：

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>要求

标头： atlcom.h

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
