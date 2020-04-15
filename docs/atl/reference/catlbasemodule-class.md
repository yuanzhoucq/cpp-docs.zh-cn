---
title: CAtlBaseModule 类
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: a55412eff18fd04ac4e41c0f001991c1cf725b9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321513"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule 类

此类在每个 ATL 项目中都实例化。

## <a name="syntax"></a>语法

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlBase模块：CAtlBase模块](#catlbasemodule)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlBase模块：：添加资源实例](#addresourceinstance)|将资源实例添加到存储句柄列表中。|
|[CAtlBase模块：：获取实例](#gethinstanceat)|将句柄返回到指定的资源实例。|
|[CAtlBase模块：获取模块实例](#getmoduleinstance)|从`CAtlBaseModule`对象返回模块实例。|
|[CAtlBase 模块：获取资源实例](#getresourceinstance)|从`CAtlBaseModule`对象返回资源实例。|
|[CAtlBase 模块：：删除资源实例](#removeresourceinstance)|从存储句柄列表中删除资源实例。|
|[CAtlBase 模块：：设置资源实例](#setresourceinstance)|设置`CAtlBaseModule`对象的资源实例。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAtlBase模块：：m_bInitFailed](#m_binitfailed)|指示模块初始化是否失败的变量。|

## <a name="remarks"></a>备注

每个 ATL 项目中都存在命名_AtlBaseModule的`CAtlBaseModule`实例，其中包含模块实例的句柄、包含资源（默认情况下为相同）的模块句柄以及提供主资源的模块的句柄数组。 `CAtlBaseModule`可以从多个线程安全地访问。

此类将替换早期版本的 ATL 中使用的过时的[CComModule](../../atl/reference/ccommodule-class.md)类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBase模块：：添加资源实例

将资源实例添加到存储句柄列表中。

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>参数

*hInst*<br/>
要添加的资源实例。

### <a name="return-value"></a>返回值

如果资源已成功添加，则返回 true，否则为 false。

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBase模块：CAtlBase模块

构造函数。

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>备注

创建 `CAtlBaseModule`。

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBase模块：：获取实例

将句柄返回到指定的资源实例。

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>参数

*Ⅰ*<br/>
资源实例的编号。

### <a name="return-value"></a>返回值

如果不存在相应的资源实例，则将句柄返回给资源实例，或返回 NULL。

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBase模块：获取模块实例

从`CAtlBaseModule`对象返回模块实例。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>返回值

返回模块实例。

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBase 模块：获取资源实例

返回资源实例。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>返回值

返回资源实例。

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBase模块：：m_bInitFailed

指示模块初始化是否失败的变量。

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>备注

如果模块初始化为 True，则为 false，如果模块未能初始化。"

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBase 模块：：删除资源实例

从存储句柄列表中删除资源实例。

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>参数

*hInst*<br/>
要删除的资源实例。

### <a name="return-value"></a>返回值

如果资源已成功删除，则返回 true，否则为 false。

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBase 模块：：设置资源实例

设置`CAtlBaseModule`对象的资源实例。

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>参数

*hInst*<br/>
新资源实例。

### <a name="return-value"></a>返回值

返回更新的资源实例。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[模块类](../../atl/atl-module-classes.md)
