---
title: '&lt;memory&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 78cdb0fe6c0d9487500804d21fe4ad4870fcad0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884062"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 枚举

## <a name="pointer_safety"></a>pointer_safety 枚举

由 `get_pointer_safety` 返回的可能值的枚举。

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>备注

范围**枚举**定义可 `get_pointer_safety()`返回的值：

`relaxed` -- 未安全派生的指针（显然是指向声明或分配对象的指针）将视为与安全派生的指针相同。

`preferred` -- 与以前一样，但不应取消引用未安全派生的指针。

`strict` -- 未安全派生的指针可能视为与安全派生的指针不同。
