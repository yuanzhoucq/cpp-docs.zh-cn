---
title: '&lt;forward_list&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: b425461f1428470b04a525efdd9a702ae038a283
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477332"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; 函数

||
|-|
|[swap](#swap)|

## <a name="swap"></a> swap

交换两个转发列表的元素。

```cpp
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*left*|一个 `forward_list` 类型的对象。|
|*right*|一个 `forward_list` 类型的对象。|

### <a name="remarks"></a>备注

该模板函数执行 `left.swap(right)`。

## <a name="see-also"></a>请参阅

[<forward_list>](../standard-library/forward-list.md)<br/>
