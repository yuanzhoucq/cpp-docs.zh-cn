---
title: '&lt;memory&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 5c5f87905b772ef277a72ef11defef8cb1001661
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494999"
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
