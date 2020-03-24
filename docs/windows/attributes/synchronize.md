---
title: 同步（C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a0f4702de4cfde8586cc573f9ff5a6195984d207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214508"
---
# <a name="synchronize"></a>synchronize

同步对目标方法的访问。

## <a name="syntax"></a>语法

```cpp
[synchronize]
```

## <a name="remarks"></a>备注

**Synchronize** C++特性实现对同步对象的目标方法的支持。 同步允许多个对象使用公共资源（如类的方法），方法是控制目标方法的访问。

此属性插入的代码在目标方法的开头调用正确的 `Lock` 方法（由线程模型确定）。 退出该方法时，会自动调用 `Unlock`。 有关这些函数的详细信息，请参阅[CComAutoThreadModule：： Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

此属性要求 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果应用 `progid`，则还会应用 `vi_progid` 和 `coclass`。

## <a name="example"></a>示例

下面的代码为 `CMyClass` 对象的 `UpdateBalance` 方法提供同步。

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|类方法、方法|
|**可重复**|否|
|**必需的特性**|以下一项或多项操作： `coclass`、`progid`或 `vi_progid`。|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[COM 特性](com-attributes.md)
