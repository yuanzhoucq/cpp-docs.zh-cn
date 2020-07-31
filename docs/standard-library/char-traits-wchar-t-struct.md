---
title: char_traits&lt;wchar_t&gt; 结构
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: 3b2504dbb124ccca7f9b27619585abb2b5795f92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219165"
---
# <a name="char_traitsltwchar_tgt-struct"></a>char_traits&lt;wchar_t&gt; 结构

一个类，该类是模板结构**char_traits \<CharType> **专用于类型的元素的 **`wchar_t`** 。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>备注

专用化允许结构利用操作此类型对象的库函数 **`wchar_t`** 。

## <a name="requirements"></a>要求

**标头：**\<string>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[char_traits 结构](../standard-library/char-traits-struct.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
