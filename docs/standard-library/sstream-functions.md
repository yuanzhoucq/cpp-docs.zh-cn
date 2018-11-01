---
title: '&lt;sstream&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: f22aec854b9a1d9b7b8360cacbb08760413fa22e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458300"
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; 函数

||
|-|
|[swap](#sstream_swap)|

## <a name="sstream_swap"></a>  swap

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

|参数|描述|
|---------------|-----------------|
|*left*|引用 `sstream` 对象。|
|*right*|引用 `sstream` 对象。|

### <a name="remarks"></a>备注

该模板函数执行 `left.swap(right)`。

## <a name="see-also"></a>请参阅

[\<sstream>](../standard-library/sstream.md)<br/>
