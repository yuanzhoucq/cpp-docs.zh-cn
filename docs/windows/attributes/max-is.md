---
title: max_is （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: dca2a3dc18aa3c3e75bbb682ed0b1b90adcd9236
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041304"
---
# <a name="maxis"></a>max_is

指定有效的数组索引的最大值。

## <a name="syntax"></a>语法

```cpp
[ max_is("expression") ]
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
|**必需的特性**|None|
|**无效的特性**|**size_is**|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>示例

请参阅[first_is](first-is.md)以举例说明如何指定数组的一部分。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameter 特性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)