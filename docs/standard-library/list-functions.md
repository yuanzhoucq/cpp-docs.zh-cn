---
title: '&lt;列表&gt;函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269019"
---
# <a name="ltlistgt-functions"></a>&lt;列表&gt;函数

## <a name="swap"></a> 交换

交换两个列表的元素。

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>参数

*左侧*\
一个 `list` 类型的对象。

*右侧*\
一个 `list` 类型的对象。

### <a name="remarks"></a>备注

该模板函数执行 `left.swap(right)`。
