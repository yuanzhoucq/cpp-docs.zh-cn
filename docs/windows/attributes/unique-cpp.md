---
title: 唯一 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.unique
dev_langs:
- C++
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca5d2da5dc06b1cdf0e999939fcb110608ff3359
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062675"
---
# <a name="unique-c"></a>unique (C++)

指定一个唯一指针。

## <a name="syntax"></a>语法

```cpp
[unique]
```

## <a name="remarks"></a>备注

**唯一**c + + 属性具有相同的功能[唯一](/windows/desktop/Midl/unique)MIDL 特性。

## <a name="example"></a>示例

请参阅[ref](ref-cpp.md)的示例使用的示例**唯一**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**typedef**， **struct**，**联合**，接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数特性](parameter-attributes.md)