---
title: 复合控件宏
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 685bf55910d4746463de30b17b71aa6d246db199
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423200"
---
# <a name="composite-control-macros"></a>复合控件宏

这些宏定义事件接收器映射和条目。

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|标记复合控件的事件接收器映射的开头。|
|[END_SINK_MAP](#end_sink_map)|标记复合控件的事件接收器映射的结尾。|
|[SINK_ENTRY](#sink_entry)|进入事件接收器映射。|
|[SINK_ENTRY_EX](#sink_entry_ex)|使用其他参数进入事件接收器映射。|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| （Visual Studio 2017）与 SINK_ENTRY_EX 类似，只不过它采用指向 iid 的指针。|
|[SINK_ENTRY_INFO](#sink_entry_info)|向事件接收器映射输入与手动提供的用于[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)的类型信息的条目。|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| （Visual Studio 2017）与 SINK_ENTRY_INFO 类似，只不过它采用指向 iid 的指针。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="begin_sink_map"></a>BEGIN_SINK_MAP

声明复合控件的事件接收器映射的开头。

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>parameters

*_class*<br/>
中指定控件。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中类型为 HRESULT 或 void 的返回值;不支持任何其他返回值，并且其行为不确定。

##  <a name="end_sink_map"></a>END_SINK_MAP

声明复合控件的事件接收器映射的结尾。

```
END_SINK_MAP()
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中类型为 HRESULT 或 void 的返回值;不支持任何其他返回值，并且其行为不确定。

##  <a name="sink_entry"></a>SINK_ENTRY

声明由*id*标识的控件的指定事件（*dispid*）的处理程序函数（*fn*）。

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>parameters

*id*<br/>
中标识控件。

*dispid*<br/>
中标识指定的事件。

*fn*<br/>
中事件处理程序函数的名称。 此函数必须使用 `_stdcall` 调用约定，并且具有适当的调度接口样式签名。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中类型为 HRESULT 或 void 的返回值;不支持任何其他返回值，并且其行为不确定。

##  <a name="sink_entry_ex"></a>SINK_ENTRY_EX 和 SINK_ENTRY_EX_P

为*id*标识的控件声明调度接口（*iid*）的指定*事件（fn）的*处理程序函数（*fn*）。

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>parameters

*id*<br/>
中标识控件。

*iid*<br/>
中标识调度接口。

*piid*<br/>
中指向调度接口的指针。

*dispid*<br/>
中标识指定的事件。

*fn*<br/>
中事件处理程序函数的名称。 此函数必须使用 `_stdcall` 调用约定，并且具有适当的调度接口样式签名。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>备注

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中类型为 HRESULT 或 void 的返回值;不支持任何其他返回值，并且其行为不确定。

##  <a name="sink_entry_info"></a>SINK_ENTRY_INFO 和 SINK_ENTRY_INFO_P

在事件接收器映射中使用 SINK_ENTRY_INFO 宏，以提供[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)将事件路由到相关处理程序函数所需的信息。

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>parameters

*id*<br/>
中标识事件源的无符号整数。 此值必须与相关[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)基类中使用的*nID*模板参数匹配。

*iid*<br/>
中IID 标识调度接口。

*piid*<br/>
中指向 IID 的指针，该指针标识调度接口。

*dispid*<br/>
中DISPID 标识指定的事件。

*fn*<br/>
中事件处理程序函数的名称。 此函数必须使用 `_stdcall` 调用约定，并且具有适当的调度接口样式签名。

info<br/>
中事件处理程序函数的类型信息。 此类型信息以指向 `_ATL_FUNC_INFO` 结构的指针的形式提供。 CC_CDECL 是 `_ATL_FUNC_INFO` 结构的 CALLCONV 字段的 Windows CE 支持的唯一选项。 不支持任何其他值，因此其行为未定义。

### <a name="remarks"></a>备注

前四个宏参数与[SINK_ENTRY_EX](#sink_entry_ex)宏的参数相同。 最终参数提供事件的类型信息。 ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中类型为 HRESULT 或 void 的返回值;不支持任何其他返回值，并且其行为不确定。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[复合控件全局函数](../../atl/reference/composite-control-global-functions.md)
