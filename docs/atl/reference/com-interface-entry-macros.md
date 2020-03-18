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
ms.openlocfilehash: 1e1674bad1164e640939d430a860beac7a6e4208
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423284"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY 宏

这些宏将对象的接口输入到其 COM 映射中，以便 `QueryInterface`可以访问这些接口。 COM 映射中条目的顺序是在 `QueryInterface`过程中，将检查排序接口的顺序。

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|将接口输入 COM 接口映射。|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用此宏消除两个继承分支。|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏可将接口输入 COM 映射，并指定其 IID。|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|与[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同，只不过您可以指定不同的 IID。|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|查询由*iid*标识的接口时，`COM_INTERFACE_ENTRY_AGGREGATE` 转发到 `punk`。|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，不同之处在于查询任何 IID 会导致将查询转发到*punk*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非*punk*为 NULL，否则将自动创建*clsid*描述的聚合。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|与[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同，不同之处在于，查询任何 IID 会导致将查询转发到*punk*，如果*punk*为 NULL，则会自动创建*clsid*描述的聚合。|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|当查询指定的接口时，使程序调用[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 。|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|为每个实例保存特定于接口的数据。|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|公开您的脱离接口。|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|当处理到达 COM 映射中的此项时，处理基类的 COM 映射。|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|用于挂钩到 ATL 的 `QueryInterface` 逻辑的一般机制。|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|与[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同，不同之处在于，查询任何 IID 都会导致调用*FUNC*。|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|当查询指定的接口时，将返回 E_NOINTERFACE 和终止 COM 映射处理。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

## <a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

将接口输入 COM 接口映射。

### <a name="syntax"></a>语法

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>parameters

*x*<br/>
中类对象直接派生自的接口的名称。

### <a name="remarks"></a>备注

通常，这是最常使用的条目类型。

### <a name="example"></a>示例

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

使用此宏消除两个继承分支。

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>parameters

*x*<br/>
中要从对象公开的接口的名称。

*x2*<br/>
中从中公开*x*的继承分支的名称。

### <a name="remarks"></a>备注

例如，如果从两个双重接口派生类对象，则会使用 COM_INTERFACE_ENTRY2 公开 `IDispatch`，因为 `IDispatch` 可从其中一个接口获得。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

使用此宏可将接口输入 COM 映射，并指定其 IID。

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>parameters

*iid*<br/>
中公开的接口的 GUID。

*x*<br/>
中类的名称，其 vtable 将公开为由*iid*标识的接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

与[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同，只不过您可以指定不同的 IID。

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>parameters

*iid*<br/>
中为接口指定的 GUID。

*x*<br/>
中类对象直接派生的接口的名称。

*x2*<br/>
中类对象直接派生的第二个接口的名称。

##  <a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

查询由*iid*标识的接口时，COM_INTERFACE_ENTRY_AGGREGATE 转发到*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>parameters

*iid*<br/>
中查询的接口的 GUID。

*punk*<br/>
中`IUnknown` 指针的名称。

### <a name="remarks"></a>备注

假定*punk*参数指向聚合的内部未知或为 NULL，在这种情况下，将忽略该条目。 通常，您将 `CoCreate` `FinalConstruct`中的聚合。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，不同之处在于查询任何 IID 会导致将查询转发到*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>parameters

*punk*<br/>
中`IUnknown` 指针的名称。

### <a name="remarks"></a>备注

如果接口查询失败，则会继续处理 COM 映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

与[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非*punk*为 NULL，否则将自动创建*clsid*描述的聚合。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>parameters

*iid*<br/>
中查询的接口的 GUID。

*punk*<br/>
中`IUnknown` 指针的名称。 必须是包含 COM 映射的类的成员。

*clsid*<br/>
中如果*punk*为 NULL，则将创建聚合的标识符。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

与[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同，不同之处在于，查询任何 IID 会导致将查询转发到*punk*，如果*punk*为 NULL，则会自动创建*clsid*描述的聚合。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>parameters

*punk*<br/>
中`IUnknown` 指针的名称。 必须是包含 COM 映射的类的成员。

*clsid*<br/>
中如果*punk*为 NULL，则将创建聚合的标识符。

### <a name="remarks"></a>备注

如果接口查询失败，则会继续处理 COM 映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

当查询指定的接口时，使程序调用[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 。

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>parameters

*x*<br/>
中用于构造接口标识符的文本。

### <a name="remarks"></a>备注

接口 IID 将通过向 `IID_`追加*x*来构造。 例如，如果*x*为 `IPersistStorage`，则将 `IID_IPersistStorage`IID。

##  <a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

为每个实例保存特定于接口的数据。

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>parameters

*iid*<br/>
中撕接口的 GUID。

*x*<br/>
中实现接口的类的名称。

*punk*<br/>
中`IUnknown` 指针的名称。 必须是包含 COM 映射的类的成员。 应在类对象的构造函数中初始化为 NULL。

### <a name="remarks"></a>备注

如果未使用接口，这将降低对象的总体实例大小。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

公开您的脱离接口。

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>parameters

*iid*<br/>
中撕接口的 GUID。

*x*<br/>
中实现接口的类的名称。

### <a name="remarks"></a>备注

一个脱离接口实现为一个单独的对象，每次查询它所代表的接口时，都会实例化该对象。 通常，如果接口很少使用，则将接口构建为脱离，因为这会在主对象的每个实例中保存 vtable 指针。 在引用计数变为零时，将删除该删除。 实现撕的类应从 `CComTearOffObjectBase` 派生，并具有自己的 COM 映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

当处理到达 COM 映射中的此项时，处理基类的 COM 映射。

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>parameters

classname<br/>
中当前对象的基类。

### <a name="remarks"></a>备注

例如，在以下代码中：

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

请注意，COM 映射中的第一项必须是包含 COM 映射的对象上的接口。 因此，您无法使用 COM_INTERFACE_ENTRY_CHAIN 启动 COM 映射条目，这会导致在对象的 COM 映射中出现**COM_INTERFACE_ENTRY_CHAIN （** `COtherObject` **）** 时搜索其他对象的 com 映射。 如果要首先搜索另一对象的 COM 映射，请将 `IUnknown` 的接口条目添加到 COM 映射，然后将另一个对象的 COM 映射链接起来。 例如：

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

用于挂钩到 ATL 的 `QueryInterface` 逻辑的一般机制。

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>parameters

*iid*<br/>
中公开的接口的 GUID。

*dw*<br/>
中传递给*函数*的参数。

func<br/>
中将返回*iid*的函数指针。

### <a name="remarks"></a>备注

如果*iid*与查询的接口的 iid 匹配，则调用由*func*指定的函数。 函数的声明应为：

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

调用函数时，`pv` 指向类对象。 *Riid*参数是指正在查询的接口，`ppv` 是指向函数应将指针存储到接口的位置的指针，而*dw*是在条目中指定的参数。 函数应将 \* `ppv` 设置为 NULL，并返回 E_NOINTERFACE 或 S_FALSE （如果它选择不返回接口）。 对于 E_NOINTERFACE，COM 映射处理终止。 在 S_FALSE 的情况下，即使未返回接口指针，COM 映射处理仍将继续进行。 如果函数返回接口指针，则它应返回 S_OK。

##  <a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

与[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同，不同之处在于，查询任何 IID 都会导致调用*FUNC*。

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>parameters

*dw*<br/>
中传递给*函数*的参数。

func<br/>
中处理 COM 映射中的此项时调用的函数。

### <a name="remarks"></a>备注

任何失败都将导致在 COM 映射上继续进行处理。 如果函数返回接口指针，则它应返回 S_OK。

##  <a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

当查询指定的接口时，将返回 E_NOINTERFACE 和终止 COM 映射处理。

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>parameters

*x*<br/>
中用于构造接口标识符的文本。

### <a name="remarks"></a>备注

此宏可用于阻止在特定情况下使用接口。 例如，你可以在 COM_INTERFACE_ENTRY_AGGREGATE_BLIND 之前将此宏插入 COM 映射，以防止将接口查询转发到聚合的内部未知。

接口 IID 将通过向 `IID_`追加*x*来构造。 例如，如果*x*为 `IPersistStorage`，则将 `IID_IPersistStorage`IID。
