---
title: max_is （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: b4931962febb1e68701aa3fe271e08f3aa8d9238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166752"
---
# <a name="max_is"></a>max_is

指定有效数组索引的最大值。

## <a name="syntax"></a>语法

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>parameters

*expression*<br/>
一个或多个 C 语言表达式。 允许空参数槽。

## <a name="remarks"></a>备注

**Max_is** C++特性具有与[max_is](/windows/win32/Midl/max-is) MIDL 特性相同的功能。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**结构**或**联合**中的字段，接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**size_is**|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>示例

有关如何指定数组的部分的示例，请参阅[first_is](first-is.md) 。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
