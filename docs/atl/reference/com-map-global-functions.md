---
title: COM 映射全局函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: c4ce7c7a68c0744ad65ef4914088fa12d3340628
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326694"
---
# <a name="com-map-global-functions"></a>COM 映射全局函数

这些函数为 COM 映射`IUnknown`实现提供支持。

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|委托给`IUnknown`非聚合对象的。|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|生成用于比较接口与`IUnknown`的有效代码。|

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>atl 内部查询接口

检索指向所请求的接口的指针。

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*p*<br/>
[在]指向对象的指针，其中包含向 公开的接口的 COM 映射`QueryInterface`。

*p条目*<br/>
[在]访问可用接口`_ATL_INTMAP_ENTRY`映射的结构数组。

*Iid*<br/>
[在]请求的接口的 GUID。

*ppvObject*<br/>
[出]指向*iid*中指定的接口指针，如果找不到接口，则指向 NULL 中的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

`AtlInternalQueryInterface` 仅处理 COM 映射表中的接口。 如果对象是聚合的，`AtlInternalQueryInterface`则不委托给外部未知对象。 您可以使用宏[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其变体之一在 COM 地图表中输入接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>内联不相等

调用此函数，用于 测试`IUnknown`的特殊情况。

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>参数

*rguid1*<br/>
[在]要与`IID_IUnknown`的 GUID 进行比较。

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[COM 映射宏](../../atl/reference/com-map-macros.md)
