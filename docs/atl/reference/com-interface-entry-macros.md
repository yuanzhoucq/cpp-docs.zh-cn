---
title: COM 接口入口宏
ms.date: 03/28/2017
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: bb7498f639f463290a4a6593ef7c0fbac09b539b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326680"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY宏

这些宏在其 COM 映射中输入对象的接口，以便可以访问`QueryInterface`它们。 COM 映射中的条目顺序是，将在 期间`QueryInterface`检查匹配的 IID 的顺序接口。

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|将接口输入 COM 接口映射。|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用此宏可以消除继承的两个分支的歧义。|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏将接口输入 COM 地图并指定其 IID。|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|与[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同 ，但可以指定其他 IID 除外。|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|查询*iid*标识的接口时，`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同 ，只不过查询任何 IID 会导致将查询转发到*punk*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非*朋克*为 NULL，否则它会自动创建*clsid*描述的聚合。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|与[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同 ，只不过查询任何 IID 会导致将查询转发到*punk*，如果*punk*为 NULL，则会自动创建*clsid*描述的聚合。|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|当查询指定的接口时，导致程序调用[DebugBreak。](/windows/win32/api/debugapi/nf-debugapi-debugbreak)|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|为每个实例保存特定于接口的数据。|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|公开拆解接口。|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|当处理到达 COM 映射中的此条目时，处理基类的 COM 映射。|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|一种连接到 ATL 逻辑的`QueryInterface`一般机制。|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|与[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同 ，只不过查询任何 IID 都会导致对*func*的调用。|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|E_NOINTERFACE返回并终止指定的接口时的 COM 映射处理。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

将接口输入 COM 接口映射。

### <a name="syntax"></a>语法

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]类对象直接派生的接口的名称。

### <a name="remarks"></a>备注

通常，这是最常用的条目类型。

### <a name="example"></a>示例

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

使用此宏可以消除继承的两个分支的歧义。

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>参数

** x <br/>
[在]要从对象公开的接口的名称。

*x2*<br/>
[在]从中公开*x*的继承分支的名称。

### <a name="remarks"></a>备注

例如，如果从两个双接口派生类对象，则使用COM_INTERFACE_ENTRY2公开`IDispatch`，因为`IDispatch`可以从任一接口获取。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

使用此宏将接口输入 COM 地图并指定其 IID。

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]接口的 GUID 暴露。

** x <br/>
[在]其 vtable 将作为*iid*标识的接口的类的名称。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

与[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同 ，但可以指定其他 IID 除外。

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]您为接口指定的 GUID。

** x <br/>
[在]类对象直接派生的接口的名称。

*x2*<br/>
[在]类对象直接派生的第二个接口的名称。

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

当查询*iid*标识的接口时，COM_INTERFACE_ENTRY_AGGREGATE转发到*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]查询的接口的 GUID。

*朋 克*<br/>
[在]`IUnknown`指针的名称。

### <a name="remarks"></a>备注

假定*punk*参数指向聚合或 NULL 的内部未知值，在这种情况下，该条目将被忽略。 通常，您将`CoCreate`中的聚合在`FinalConstruct`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同 ，只不过查询任何 IID 会导致将查询转发到*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]`IUnknown`指针的名称。

### <a name="remarks"></a>备注

如果接口查询失败，则处理 COM 映射将继续。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非*朋克*为 NULL，否则它会自动创建*clsid*描述的聚合。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]查询的接口的 GUID。

*朋 克*<br/>
[在]`IUnknown`指针的名称。 必须是包含 COM 映射的类的成员。

*Clsid*<br/>
[在]如果*punk*为 NULL，则要创建的聚合的标识符。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

与[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同 ，只不过查询任何 IID 会导致将查询转发到*punk*，如果*punk*为 NULL，则会自动创建*clsid*描述的聚合。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]`IUnknown`指针的名称。 必须是包含 COM 映射的类的成员。

*Clsid*<br/>
[在]如果*punk*为 NULL，则要创建的聚合的标识符。

### <a name="remarks"></a>备注

如果接口查询失败，则处理 COM 映射将继续。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

当查询指定的接口时，导致程序调用[DebugBreak。](/windows/win32/api/debugapi/nf-debugapi-debugbreak)

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>参数

** x <br/>
[在]用于构造接口标识符的文本。

### <a name="remarks"></a>备注

接口 IID 将通过将*x*追加到`IID_`来构造。 例如，如果*x* `IPersistStorage`是 ，则 IID 将为`IID_IPersistStorage`。

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

为每个实例保存特定于接口的数据。

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]撕裂接口的 GUID。

** x <br/>
[在]实现接口的类的名称。

*朋 克*<br/>
[在]`IUnknown`指针的名称。 必须是包含 COM 映射的类的成员。 应在类对象的构造函数中初始化为 NULL。

### <a name="remarks"></a>备注

如果未使用接口，这将降低对象的总体实例大小。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

公开拆解接口。

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]撕裂接口的 GUID。

** x <br/>
[在]实现接口的类的名称。

### <a name="remarks"></a>备注

拆解接口作为单独的对象实现，每次查询它所代表的接口时都会实例化该对象。 通常，如果很少使用接口，则可以将接口构建为分机，因为这会在主对象的每个实例中保存一个 vtable 指针。 当其引用计数变为零时，将删除拆解。 实现分泪的类应派生自`CComTearOffObjectBase`并有自己的 COM 映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

当处理到达 COM 映射中的此条目时，处理基类的 COM 映射。

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>参数

*类名*<br/>
[在]当前对象的基类。

### <a name="remarks"></a>备注

例如，在以下代码中：

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

请注意，COM 地图中的第一个条目必须是包含 COM 贴图的对象上的接口。 因此，您不能用COM_INTERFACE_ENTRY_CHAIN启动 COM 贴图条目，这将导致在对象 COM 地图中出现**COM_INTERFACE_ENTRY_CHAIN（）**`COtherObject`**)** 点搜索其他对象的 COM 贴图。 如果要首先搜索另一个对象的 COM 贴图，请向`IUnknown`COM 贴图添加接口条目，然后链接另一个对象的 COM 贴图。 例如：

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

一种连接到 ATL 逻辑的`QueryInterface`一般机制。

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]接口的 GUID 暴露。

*dw*<br/>
[在]参数传递给*func*。

*func*<br/>
[在]将返回*iid 的*函数指针。

### <a name="remarks"></a>备注

如果*iid*与所查询的接口的 IID 匹配，则调用*func*指定的函数。 函数的声明应为：

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

调用函数时，`pv`将指向类对象。 *riid*参数是指要查询的接口，`ppv`是指向函数应存储指向接口的指针的位置的指针 *，dw*是您在条目中指定的参数。 如果函数选择不返回\*`ppv`接口，则该函数应设置为 NULL 并返回E_NOINTERFACE或S_FALSE。 使用E_NOINTERFACE，COM 映射处理将终止。 使用S_FALSE，即使未返回接口指针，COM 映射处理仍将继续。 如果函数返回接口指针，则应返回S_OK。

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

与[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同 ，只不过查询任何 IID 都会导致对*func*的调用。

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>参数

*dw*<br/>
[在]参数传递给*func*。

*func*<br/>
[在]处理 COM 地图中的此条目时调用的函数。

### <a name="remarks"></a>备注

任何故障都将导致处理在 COM 地图上继续。 如果函数返回接口指针，则应返回S_OK。

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

E_NOINTERFACE返回并终止指定的接口时的 COM 映射处理。

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>参数

** x <br/>
[在]用于构造接口标识符的文本。

### <a name="remarks"></a>备注

可以使用此宏防止在特定情况下使用接口。 例如，可以在COM_INTERFACE_ENTRY_AGGREGATE_BLIND之前将此宏插入到 COM 地图中，以防止将接口的查询转发到聚合的内部未知。

接口 IID 将通过将*x*追加到`IID_`来构造。 例如，如果*x* `IPersistStorage`是 ，则 IID 将为`IID_IPersistStorage`。
