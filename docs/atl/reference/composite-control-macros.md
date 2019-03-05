---
title: 复合控件宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 2c6d3e350755ef4a0cf4a84561e34619ab3974be
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299107"
---
# <a name="composite-control-macros"></a>复合控件宏

这些宏定义事件接收器映射和条目。

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|表示复合控件的事件接收器映射的开头。|
|[END_SINK_MAP](#end_sink_map)|表示复合控件的事件接收器映射的结尾。|
|[SINK_ENTRY](#sink_entry)|事件接收器映射到的项。|
|[SINK_ENTRY_EX](#sink_entry_ex)|进入事件接收器映射带有一个附加参数。|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017)类似 SINK_ENTRY_EX，只不过它采用一个指向 iid。|
|[SINK_ENTRY_INFO](#sink_entry_info)|手动提供的类型信息以用于与事件接收器映射到条目[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)。|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017)类似 SINK_ENTRY_INFO，只不过它采用一个指向 iid。|

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="begin_sink_map"></a>  BEGIN_SINK_MAP

声明的复合控件的事件接收器映射的开头。

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>参数

*_class*<br/>
[in]指定的控件。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或 void 从在事件处理程序方法; 这些方法任何其他返回值是不受支持，而且其行为是未定义。

##  <a name="end_sink_map"></a>  END_SINK_MAP

声明的复合控件的事件接收器映射的末尾。

```
END_SINK_MAP()
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或 void 从在事件处理程序方法; 这些方法任何其他返回值是不受支持，而且其行为是未定义。

##  <a name="sink_entry"></a>  SINK_ENTRY

声明处理程序函数 (*fn*) 为指定的事件 (*dispid*)，标识控件的*id*。

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>参数

*id*<br/>
[in]标识控件。

*dispid*<br/>
[in]标识在指定的事件。

*fn*<br/>
[in]事件处理程序函数的名称。 此函数必须使用`_stdcall`调用约定和具有适当的调度接口风格的签名。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或 void 从在事件处理程序方法; 这些方法任何其他返回值是不受支持，而且其行为是未定义。

##  <a name="sink_entry_ex"></a>  SINK_ENTRY_EX 和 SINK_ENTRY_EX_P

声明处理程序函数 (*fn*) 为指定的事件 (*dispid*)，调度接口 (*iid*)，用于标识的控件*id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*id*<br/>
[in]标识控件。

*iid*<br/>
[in]标识调度接口。

*piid*<br/>
[in]指向调度接口指针。

*dispid*<br/>
[in]标识在指定的事件。

*fn*<br/>
[in]事件处理程序函数的名称。 此函数必须使用`_stdcall`调用约定和具有适当的调度接口风格的签名。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>备注

CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或 void 从在事件处理程序方法; 这些方法任何其他返回值是不受支持，而且其行为是未定义。

##  <a name="sink_entry_info"></a>  SINK_ENTRY_INFO 和 SINK_ENTRY_INFO_P

使用事件接收器映射内的 SINK_ENTRY_INFO 宏来提供所需的信息[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)事件路由到相关的处理程序函数。

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*id*<br/>
[in]标识事件源的无符号的整数。 此值必须匹配*nID*中的相关使用的模板参数[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)基类。

*iid*<br/>
[in]标识调度接口的 IID。

*piid*<br/>
[in]指针，指向标识调度接口的 IID。

*dispid*<br/>
[in]确定指定的事件的 DISPID。

*fn*<br/>
[in]事件处理程序函数的名称。 此函数必须使用`_stdcall`调用约定和具有适当的调度接口风格的签名。

info<br/>
[in]类型的事件处理程序函数的信息。 指向的指针的形式提供此类型信息`_ATL_FUNC_INFO`结构。 CC_CDECL 是唯一的选项在 Windows CE 中支持的 CALLCONV 字段`_ATL_FUNC_INFO`结构。 任何其他值不受支持因此其行为未定义。

### <a name="remarks"></a>备注

前四个宏参数是否与用于相同[SINK_ENTRY_EX](#sink_entry_ex)宏。 最后一个参数提供事件的类型信息。 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或 void 从在事件处理程序方法; 这些方法任何其他返回值是不受支持，而且其行为是未定义。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[复合控件全局函数](../../atl/reference/composite-control-global-functions.md)
