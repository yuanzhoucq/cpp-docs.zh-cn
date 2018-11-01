---
title: 对象 （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 1cae9e6b014f33dfbbcccdeb4172d6f35349e307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526148"
---
# <a name="object-c"></a>object (C++)

标识的自定义的接口。

## <a name="syntax"></a>语法

```cpp
[object]
```

## <a name="remarks"></a>备注

前面的接口定义中，当**对象**c + + 属性导致将接口置于.idl 文件作为自定义的接口。

使用对象标记任何接口必须继承自`IUnknown`。 如果从任何基接口继承，则满足此条件`IUnknown`。 如果没有基接口继承自`IUnknown`，编译器将导致使用标记的接口**对象**为派生`IUnknown`。

## <a name="example"></a>示例

请参阅[nonbrowsable](nonbrowsable.md)有关如何使用的示例**对象**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)