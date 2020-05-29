---
title: 复合控制宏
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 67ad18c07a92cfecca44667908a8488e8c2da234
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331519"
---
# <a name="composite-control-macros"></a>复合控制宏

这些宏定义事件接收器映射和条目。

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|标记复合控件的事件接收器映射的开头。|
|[END_SINK_MAP](#end_sink_map)|标记复合控件的事件接收器映射的末尾。|
|[SINK_ENTRY](#sink_entry)|进入事件接收器映射。|
|[SINK_ENTRY_EX](#sink_entry_ex)|使用附加参数进入事件接收器映射。|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| （视觉工作室 2017）类似于SINK_ENTRY_EX，只不过它需要指向 iid 的指针。|
|[SINK_ENTRY_INFO](#sink_entry_info)|条目事件接收器映射与手动提供的类型信息，用于与[IDispEventSimple.](../../atl/reference/idispeventsimpleimpl-class.md)|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| （视觉工作室 2017）类似于SINK_ENTRY_INFO，只不过它需要指向 iid 的指针。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP

声明复合控件的事件接收器映射的开头。

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>参数

*_class*<br/>
[在]指定控件。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中 HRESULT 类型的返回值或 void;任何其他返回值不受支持，其行为未定义。

## <a name="end_sink_map"></a><a name="end_sink_map"></a>END_SINK_MAP

声明复合控件的事件接收器映射的结束。

```
END_SINK_MAP()
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中 HRESULT 类型的返回值或 void;任何其他返回值不受支持，其行为未定义。

## <a name="sink_entry"></a><a name="sink_entry"></a>SINK_ENTRY

声明*ID*标识的控件的指定事件 （*不pid）* 的处理程序函数 *（fn*）。

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]标识控件。

*不一部分*<br/>
[在]标识指定的事件。

*Fn*<br/>
[在]事件处理程序函数的名称。 此函数必须使用`_stdcall`调用约定，并具有适当的非接口样式签名。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中 HRESULT 类型的返回值或 void;任何其他返回值不受支持，其行为未定义。

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX和SINK_ENTRY_EX_P

声明调度接口 *（iid）* 的指定事件 （*不pid）* 的处理程序函数 *（fn），* 用于*由 id*标识的控件。

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*id*<br/>
[在]标识控件。

*Iid*<br/>
[在]标识调度接口。

*皮伊德*<br/>
[在]指向调度接口的指针。

*不一部分*<br/>
[在]标识指定的事件。

*Fn*<br/>
[在]事件处理程序函数的名称。 此函数必须使用`_stdcall`调用约定，并具有适当的非接口样式签名。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中 HRESULT 类型的返回值或 void;任何其他返回值不受支持，其行为未定义。

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a>SINK_ENTRY_INFO和SINK_ENTRY_INFO_P

使用事件接收器映射中的SINK_ENTRY_INFO宏来提供[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)所需的信息，以将事件路由到相关的处理程序函数。

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*id*<br/>
[在]标识事件源的无符号整数。 此值必须与相关[IDispEventSimple](../../atl/reference/idispeventsimpleimpl-class.md)基础类中使用的*nID*模板参数匹配。

*Iid*<br/>
[在]标识调度接口的 IID。

*皮伊德*<br/>
[在]指向标识派单接口的 IID 的指针。

*不一部分*<br/>
[在]识别指定事件的 DISPID。

*Fn*<br/>
[在]事件处理程序函数的名称。 此函数必须使用`_stdcall`调用约定，并具有适当的非接口样式签名。

info**<br/>
[在]键入事件处理程序函数的信息。 此类型信息以指向`_ATL_FUNC_INFO`结构的指针的形式提供。 CC_CDECL是`_ATL_FUNC_INFO`Windows CE 中支持结构 CALLCONV 字段的唯一选项。 任何其他值不受支持，因此其行为未定义。

### <a name="remarks"></a>备注

前四个宏参数与[SINK_ENTRY_EX](#sink_entry_ex)宏的参数相同。 最终参数提供事件的类型信息。 ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中 HRESULT 类型的返回值或 void;任何其他返回值不受支持，其行为未定义。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[复合控件全局函数](../../atl/reference/composite-control-global-functions.md)
