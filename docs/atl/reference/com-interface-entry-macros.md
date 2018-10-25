---
title: COM 接口入口宏 |Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16aa17ef58e8e4a7f0b8970cb229b6c914f291fe
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080112"
---
# <a name="cominterfaceentry-macros"></a>COM_INTERFACE_ENTRY 宏

这些宏的对象的接口输入到其 COM 映射，以便可以通过访问这些`QueryInterface`。 COM 映射中的条目的顺序是顺序接口将检查期间匹配 IID `QueryInterface`。

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|将接口输入到 COM 接口映射。|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用此宏来消除两个分支的继承。|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏以输入到 COM 映射的接口，并指定其 IID。|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|与相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，但您可以指定不同的 IID。|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|标识接口*iid* ，查询`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，只不过查询任何 IID 导致转发到查询*punk*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非*punk*为 NULL，它会自动创建所描述的聚合*clsid*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|与相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，只不过查询任何 IID 导致转发到查询*punk*，并且如果*punk*为 NULL，会自动创建所描述的聚合*clsid*。|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|导致你的程序来调用[DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297)时为查询指定的接口。|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|将保存每个实例的特定于接口的数据。|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|公开您分离式接口。|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|当处理到达的 COM 映射中的此条目时处理的基类的 COM 映射。|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|以挂钩到 ATL 的常规机制`QueryInterface`逻辑。|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|与相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，只不过对的调用中查询任何 IID 结果*func*。|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|将返回 E_NOINTERFACE 和终止时为查询指定的接口的 COM 映射处理。|

## <a name="requirements"></a>要求

**标头：** atlcom.h

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY

将接口输入到 COM 接口映射。

### <a name="syntax"></a>语法

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>参数

*x*<br/>
[in]直接从派生类对象的接口的名称。

### <a name="remarks"></a>备注

通常情况下，这是最常使用的条目类型。

### <a name="example"></a>示例

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="com_interface_entry2"></a>  COM_INTERFACE_ENTRY2

使用此宏来消除两个分支的继承。

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>参数

*x*<br/>
[in]要从您的对象公开的接口的名称。

*x2*<br/>
[in]从其继承分支的名称*x*得以实现。

### <a name="remarks"></a>备注

例如，如果派生类对象从两个双重接口，您公开`IDispatch`使用自 COM_INTERFACE_ENTRY2`IDispatch`可以从任一接口获取。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID

使用此宏以输入到 COM 映射的接口，并指定其 IID。

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]公开的接口的 GUID。

*x*<br/>
[in]将作为由标识的接口公开其 vtable 的类的名称*iid*。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID

与相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，但您可以指定不同的 IID。

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]您在指定的接口的 GUID。

*x*<br/>
[in]直接从派生类对象的接口的名称。

*x2*<br/>
[in]第二个接口直接派生类对象的名称。

##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE

标识接口*iid*为 COM_INTERFACE_ENTRY_AGGREGATE 将转发到查询*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]查询的接口的 GUID。

*punk*<br/>
[in]名称`IUnknown`指针。

### <a name="remarks"></a>备注

*Punk*参数则假定以指向内部聚合的未知或为 NULL，这种情况下该条目将被忽略。 通常情况下，将`CoCreate`中的聚合`FinalConstruct`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND

与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，只不过查询任何 IID 导致转发到查询*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>参数

*punk*<br/>
[in]名称`IUnknown`指针。

### <a name="remarks"></a>备注

如果接口查询将失败，继续进行处理的 COM 映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE

与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非*punk*为 NULL，它会自动创建所描述的聚合*clsid*。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]查询的接口的 GUID。

*punk*<br/>
[in]名称`IUnknown`指针。 必须是类的包含 COM 映射的成员。

*clsid*<br/>
[in]如果将创建的聚合标识符*punk*为 NULL。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

与相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，只不过查询任何 IID 导致转发到查询*punk*，并且如果*punk*为 NULL，会自动创建所描述的聚合*clsid*。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>参数

*punk*<br/>
[in]名称`IUnknown`指针。 必须是类的包含 COM 映射的成员。

*clsid*<br/>
[in]如果将创建的聚合标识符*punk*为 NULL。

### <a name="remarks"></a>备注

如果接口查询将失败，继续进行处理的 COM 映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK

导致你的程序来调用[DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297)时为查询指定的接口。

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>参数

*x*<br/>
[in]用于构造的接口标识符的文本。

### <a name="remarks"></a>备注

将通过追加构造 IID 的接口*x*到`IID_`。 例如，如果*x*是`IPersistStorage`，将 IID `IID_IPersistStorage`。

##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

将保存每个实例的特定于接口的数据。

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]分离式接口的 GUID。

*x*<br/>
[in]实现该接口的类的名称。

*punk*<br/>
[in]名称`IUnknown`指针。 必须是类的包含 COM 映射的成员。 应在类对象的构造函数中初始化为 NULL。

### <a name="remarks"></a>备注

如果不使用此接口，这会降低您的对象的总体实例大小。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF

公开您分离式接口。

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]分离式接口的 GUID。

*x*<br/>
[in]实现该接口的类的名称。

### <a name="remarks"></a>备注

因为每次该接口表示实例化一个单独的对象查询的实现分离式接口。 通常情况下，你生成接口为分离式如果很少使用此接口，因为这将 vtable 指针保存在您的主要对象的每个实例。 拖曳时将删除其引用计数变为零。 实现分离式的类应派生自`CComTearOffObjectBase`并具有其自己的 COM 映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN

当处理到达的 COM 映射中的此条目时处理的基类的 COM 映射。

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>参数

classname<br/>
[in]当前对象的基类。

### <a name="remarks"></a>备注

例如，在以下代码：

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

请注意，COM 映射中的第一个条目必须包含 COM 映射的对象上的接口。 因此，不能将您的 COM 映射项开头 COM_INTERFACE_ENTRY_CHAIN，这会导致不同的对象要在其中搜索点的 COM 映射其中**COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** 对象的 COM 映射中显示。 如果你想要首先搜索另一个对象的 COM 映射，将添加的接口条目`IUnknown`到 COM 映射，然后链接对象的 COM 映射。 例如：

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC

以挂钩到 ATL 的常规机制`QueryInterface`逻辑。

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]公开的接口的 GUID。

*数据仓库*<br/>
[in]一个参数传递给*func*。

*func*<br/>
[in]将返回的函数指针*iid*。

### <a name="remarks"></a>备注

如果*iid*匹配的查询，该接口然后由指定的函数的 IID *func*调用。 该函数的声明应为：

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

当调用函数时，`pv`指向类对象。 *Riid*参数是指对其进行查询，该接口`ppv`是一个指针指向该函数应在其中存储接口的指针的位置和*dw*是参数，在项中指定。 该函数应设置\*`ppv`为 NULL 并返回 E_NOINTERFACE 或如果它选择不返回接口返回 S_FALSE。 E_NOINTERFACE，与 COM 映射处理终止。 S_FALSE，与 COM 映射继续进行处理，即使没有接口指针返回。 如果该函数返回的接口指针，则应返回 S_OK。

##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND

与相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，只不过对的调用中查询任何 IID 结果*func*。

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>参数

*数据仓库*<br/>
[in]一个参数传递给*func*。

*func*<br/>
[in]获取处理 COM 映射中的此条目时调用的函数。

### <a name="remarks"></a>备注

任何失败将导致处理 COM 映射上继续。 如果该函数返回的接口指针，则应返回 S_OK。

##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE

将返回 E_NOINTERFACE 和终止时为查询指定的接口的 COM 映射处理。

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>参数

*x*<br/>
[in]用于构造的接口标识符的文本。

### <a name="remarks"></a>备注

此宏可用于防止在特定情况下使用一个接口。 例如，您可以插入之前 COM_INTERFACE_ENTRY_AGGREGATE_BLIND 以防止该接口的查询转发到聚合的内部未知在 COM 映射此宏。

将通过追加构造 IID 的接口*x*到`IID_`。 例如，如果*x*是`IPersistStorage`，将 IID `IID_IPersistStorage`。

