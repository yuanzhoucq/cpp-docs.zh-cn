---
title: size_is |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0505fde4ea92c643a6038d64d10ec06cda9cb60d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392328"
---
# <a name="sizeis"></a>size_is

指定的内存大小为固定大小的指针分配、 调整大小的指针和单字节或多维数组的指针。

## <a name="syntax"></a>语法

```cpp
[ size_is(
   "expression"
) ]
```

### <a name="parameters"></a>参数

*表达式*<br/>
为分配的内存大小的大小调整指针。

## <a name="remarks"></a>备注

**Size_is** c + + 属性具有相同的功能[size_is](/windows/desktop/Midl/size-is) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[first_is](../windows/first-is.md)有关如何指定数组的一个部分的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|中的字段**struct**或**union**，接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`max_is`|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[参数特性](../windows/parameter-attributes.md)<br/>
[first_is](../windows/first-is.md)<br/>
[last_is](../windows/last-is.md)<br/>
[max_is](../windows/max-is.md)<br/>
[length_is](../windows/length-is.md)  