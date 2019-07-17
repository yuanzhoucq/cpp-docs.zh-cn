---
title: '&lt;forward_list&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240668"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; 函数

## <a name="swap"></a> 交换

交换两个转发列表的元素。

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*左侧*\
一个 `forward_list` 类型的对象。

*右侧*\
一个 `forward_list` 类型的对象。

### <a name="remarks"></a>备注

该模板函数执行 `left.swap(right)`。
