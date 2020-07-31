---
title: 聚合（c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregates
helpviewer_keywords:
- aggregates attribute
- aggregation [C++]
- aggregate objects [C++], aggregates attribute
- aggregates [C++]
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
ms.openlocfilehash: 65a166faa9380272c87af92ebaf8294c0e0b1af3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217280"
---
# <a name="aggregates"></a>aggregates

指示对象聚合由 CLSID 指定的对象。

## <a name="syntax"></a>语法

```cpp
[ aggregates(clsid, variable_name) ]
```

### <a name="parameters"></a>参数

*clsid*<br/>
指定可聚合对象的 CLSID。

*variable_name*<br/>
要插入的变量的名称。 此变量包含所 `IUnknown` 聚合的对象的。

## <a name="remarks"></a>备注

应用于对象时， **aggregates** C++ 属性会为所聚合的对象（由 `clsid`指定）实现外部包装器。

此属性要求 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果 `progid` 应用了，则 `vi_progid` `coclass` 还会应用。

### <a name="atl-projects"></a>ATL 项目

如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 首先，将以下条目添加到目标对象的 COM 映射：

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)
```

其次，还会添加 [DECLARE_GET_CONTROLLING_UNKNOWN](../../atl/reference/aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) 宏。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_aggregates.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

// requires 'aggregatable.dll'
// see aggregatable attribute to create 'aggregatable.dll'
class DECLSPEC_UUID("1a8369cc-1c91-42c4-befa-5a5d8c9d2529") CMyClass;

[module (name="MYObject")];
[object, uuid("ab006d85-e754-47c5-9ef4-2744ff32a20c")]
__interface IObject
{
};

[ coclass, aggregates(__uuidof(CMyClass)),
  uuid("91cb2c06-8931-432a-baac-206e55c4edfb")]
struct CObject : IObject
{
   int i;
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|是|
|**必需属性**|以下一项或多项操作： `coclass` 、 `progid` 或 `vi_progid` 。|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[COM 特性](com-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[聚合](/windows/win32/com/aggregation)<br/>
[可](/windows/win32/Midl/aggregatable)<br/>
[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](../../atl/reference/com-interface-entry-macros.md#com_interface_entry_autoaggregate_blind)
