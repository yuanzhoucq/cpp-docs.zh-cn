---
title: last_is （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: 7aa8acb52d19bc7f70513e44770817ae7fc403b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224404"
---
# <a name="last_is"></a>last_is

指定要传输的最后一个数组元素的索引。

## <a name="syntax"></a>语法

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>参数

*expression*<br/>
一个或多个 C 语言表达式。 允许空参数槽。

## <a name="remarks"></a>备注

**Last_is** c + + 特性具有与[last_is](/windows/win32/Midl/last-is) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何指定数组的部分的示例，请参阅[first_is](first-is.md) 。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|或中的字段 **`struct`** **`union`** ，接口参数，接口方法|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数属性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
