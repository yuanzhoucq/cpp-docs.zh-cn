---
title: is_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 339b3cdb2e2470fea976ef8257e6a84f089d3dd9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712551"
---
# <a name="isassignable-class"></a>is_assignable 类

测试 `From` 类型的值是否可以分配给 `To` 类型。

## <a name="syntax"></a>语法

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>参数

*若要*<br/>
接收赋值的对象的类型。

*From*<br/>
提供值的对象的类型。

## <a name="remarks"></a>备注

未计算的表达式 `declval<To>() = declval<From>()` 必须具有正确格式。 这两`From`并`To`必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
