---
title: '&lt;memory&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: b2f5b50dc1344b95e88742d346e32fc55f821336
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243851"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 枚举

## <a name="pointer_safety"></a> pointer_safety 枚举

由 `get_pointer_safety` 返回的可能值的枚举。

```
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>备注

指定了作用域**enum**定义可由返回的值`get_pointer_safety()`:

`relaxed` -- 未安全派生的指针（显然是指向声明或分配对象的指针）将视为与安全派生的指针相同。

`preferred` -- 与以前一样，但不应取消引用未安全派生的指针。

`strict` -- 未安全派生的指针可能视为与安全派生的指针不同。
