---
title: '&lt;memory&gt; 枚举 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 9b9ea485bb66292c3c0509036c22dd161a694dd3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961406"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 枚举

||
|-|
|[pointer_safety](#pointer_safety)|

## <a name="pointer_safety"></a>pointer_safety 枚举

由 `get_pointer_safety` 返回的可能值的枚举。

class pointer_safety { relaxed, preferred, strict };

### <a name="remarks"></a>备注

指定了作用域**enum**定义可由返回的值`get_pointer_safety()`:

`relaxed` -- 未安全派生的指针（显然是指向声明或分配对象的指针）将视为与安全派生的指针相同。

`preferred` -- 与以前一样，但不应取消引用未安全派生的指针。

`strict` -- 未安全派生的指针可能视为与安全派生的指针不同。

## <a name="see-also"></a>请参阅

[\<memory>](../standard-library/memory.md)<br/>
