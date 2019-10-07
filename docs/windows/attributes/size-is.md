---
title: size_is (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 504f1bf72b8ffa15e8df50bb00c86ef909688f1e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514037"
---
# <a name="size_is"></a>size_is

指定分配给大小指针的内存大小、大小指针的大小指针以及单数组或多维数组。

## <a name="syntax"></a>语法

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>参数

expression<br/>
为大小指针分配的内存的大小。

## <a name="remarks"></a>备注

**Size_is** C++特性具有与[size_is](/windows/win32/Midl/size-is) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何指定数组的部分的示例, 请参阅[first_is](first-is.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**结构**或**联合**中的字段, 接口参数, 接口方法|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|`max_is`|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)