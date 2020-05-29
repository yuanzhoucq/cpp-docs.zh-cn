---
title: '&lt;sstream&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: bdf7cd26b25680eb7e5270fdc8ae7dac0d10f70f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336657"
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; 函数

||
|-|
|[交换](#sstream_swap)|

## <a name="swap"></a><a name="sstream_swap"></a>交换

交换两个 `sstream` 对象间的值。

```cpp
template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,
    basic_stringstream<Elem, Tr, Alloc>& right);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*离开*|引用 `sstream` 对象。|
|*对*|引用 `sstream` 对象。|

### <a name="remarks"></a>备注

该模板函数执行 `left.swap(right)`。

## <a name="see-also"></a>另请参阅

[\<溪流>](../standard-library/sstream.md)
