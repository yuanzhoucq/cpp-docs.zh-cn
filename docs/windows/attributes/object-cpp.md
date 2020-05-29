---
title: object （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 4545d899c13a1eabf8ea5fb6fe3918fb5f05b626
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214646"
---
# <a name="object-c"></a>object (C++)

标识自定义接口。

## <a name="syntax"></a>语法

```cpp
[object]
```

## <a name="remarks"></a>备注

在接口定义前面时，**对象** C++特性会导致接口作为自定义接口放置在 .idl 文件中。

标记有对象的任何接口都必须继承自 `IUnknown`。 如果任何基接口从 `IUnknown`继承，则满足此条件。 如果没有基接口继承自 `IUnknown`，编译器将导致用**对象**标记的接口从 `IUnknown`派生。

## <a name="example"></a>示例

有关如何使用**对象**的示例，请参阅[nonbrowsable](nonbrowsable.md) 。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
