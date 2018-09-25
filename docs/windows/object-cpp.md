---
title: 对象 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e1cf7f100c34023e6fea96c9764cce2371dcaaf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412685"
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

请参阅[nonbrowsable](../windows/nonbrowsable.md)有关如何使用的示例**对象**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[接口特性](../windows/interface-attributes.md)<br/>
[dual](../windows/dual.md)<br/>
[dispinterface](../windows/dispinterface.md)<br/>
[custom](../windows/custom-cpp.md)<br/>
[__interface](../cpp/interface.md)  