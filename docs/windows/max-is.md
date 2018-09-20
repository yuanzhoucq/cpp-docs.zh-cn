---
title: max_is |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a66a849dceb5ba28eb6630b513a121e219a3588
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432952"
---
# <a name="maxis"></a>max_is

指定有效的数组索引的最大值。

## <a name="syntax"></a>语法

```cpp
[ max_is(
   "expression"
) ]
```

### <a name="parameters"></a>参数

*表达式*<br/>
一个或多个 C 语言表达式。 允许使用空参数槽。

## <a name="remarks"></a>备注

**Max_is** c + + 属性具有相同的功能[max_is](/windows/desktop/Midl/max-is) MIDL 特性。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|中的字段**struct**或**union**，接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**size_is**|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="example"></a>示例

请参阅[first_is](../windows/first-is.md)以举例说明如何指定数组的一部分。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[参数特性](../windows/parameter-attributes.md)<br/>
[first_is](../windows/first-is.md)<br/>
[last_is](../windows/last-is.md)<br/>
[length_is](../windows/length-is.md)<br/>
[size_is](../windows/size-is.md)  