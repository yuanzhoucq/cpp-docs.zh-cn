---
title: last_is （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: 39b35b218f3402839d956c4da0a00f290fe5d595
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033269"
---
# <a name="lastis"></a>last_is

指定要传输的最后一个数组元素的索引。

## <a name="syntax"></a>语法

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>参数

*表达式*<br/>
一个或多个 C 语言表达式。 允许使用空参数槽。

## <a name="remarks"></a>备注

**Last_is** c + + 属性具有相同的功能[last_is](/windows/desktop/Midl/last-is) MIDL 特性。

## <a name="example"></a>示例

请参阅[first_is](first-is.md)以举例说明如何指定数组的一部分。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|中的字段**struct**或**union**，接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameter 特性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)