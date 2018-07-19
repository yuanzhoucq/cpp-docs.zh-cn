---
title: '&lt;forward_list&gt; 函数 | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 097dca5d26014696e218ff6439b81e1d0349b2c5
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966314"
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
