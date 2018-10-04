---
title: implements_category （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.implements_category
dev_langs:
- C++
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8c7e521d4a79ad1743e87c540e984c43cad7d39
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790545"
---
# <a name="implementscategory"></a>implements_category

指定由目标类实现的组件类别。

## <a name="syntax"></a>语法

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>参数

*implements_category*<br/>
实现类别的 ID。

## <a name="remarks"></a>备注

**Implements_category** c + + 属性指定由目标类实现的组件类别。 这是通过创建类别映射并添加指定的单独条目**implements_category**属性。 有关详细信息，请参阅[组件类别和执行它们的工作原理是什么？](https://msdn.microsoft.com/library/windows/desktop/ms694322)。

此属性要求[组件类](coclass.md)， [progid](progid.md)，或[vi_progid](vi-progid.md)属性 （或隐含其中一种的另一个属性） 也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果`progid`应用时，`vi_progid`和`coclass`也会应用。

## <a name="example"></a>示例

下面的代码指定以下对象实现`Control`类别。

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|是|
|**必需的特性**|以下项之一： `coclass`， `progid`，或 `vi_progid`|
|**无效的特性**|无|

有关详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[COM 特性](com-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)  