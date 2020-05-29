---
title: pointer_default （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: d0c5832623c1e418f4c6e8bdb606d1d363503483
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166531"
---
# <a name="pointer_default"></a>pointer_default

指定所有指针的默认指针特性（在参数列表中出现的顶级指针除外）。

## <a name="syntax"></a>语法

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>parameters

*value*<br/>
一个值，用于描述指针类型： **ptr**、 **ref**或**unique**。

## <a name="remarks"></a>备注

**Pointer_default** C++特性具有与[pointer_default](/windows/win32/Midl/pointer-default) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关**pointer_default**的示例用法，请参阅[defaultvalue](defaultvalue.md)的示例。

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
[接口特性](interface-attributes.md)
