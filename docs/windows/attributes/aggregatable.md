---
title: 聚合 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0b686cd19d76706bb6a30286cf611c563c1aed50
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790353"
---
# <a name="aggregatable"></a>aggregatable

指示该类支持聚合。

## <a name="syntax"></a>语法

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>参数

*value*<br/>
（可选）用于指示何时可聚合 COM 对象的参数：

- `never` 不能聚合的 COM 对象。

- `allowed` 可以直接创建 COM 对象，或可以聚合。 这是默认设置。

- `always` COM 对象不能直接创建，并且仅可以聚合。 当您调用`CoCreateInstance`对于此对象，您必须指定聚合对象的`IUnknown`接口 (控制`IUnknown`)。

## <a name="remarks"></a>备注

**聚合**c + + 属性具有相同的功能[聚合](/windows/desktop/Midl/aggregatable)MIDL 特性。 这意味着，编译器会将传递**聚合**属性通过到生成的.idl 文件。

此属性要求[组件类](coclass.md)， [progid](progid.md)，或[vi_progid](vi-progid.md)属性 （或隐含其中一种的另一个属性） 也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果`progid`应用时，`vi_progid`和`coclass`也会应用。

### <a name="atl-projects"></a>ATL 项目

如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 除了前面所述的行为，该属性还将添加以下宏之一到目标类：

|参数值|插入的宏|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|一个或多个以下： `coclass`， `progid`，或`vi_progid`。|
|**无效的特性**|无|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[聚合](/windows/desktop/com/aggregation)  