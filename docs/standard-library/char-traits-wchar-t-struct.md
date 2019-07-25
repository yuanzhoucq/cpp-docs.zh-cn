---
title: char_traits&lt;wchar_t&gt; 结构
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: a2f8a882020ddb3d87436d08b3d85ea9407b1c08
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458968"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 结构

一个类, 该类是模板结构**char_traits\<CharType >** 的专用化到**wchar_t**类型的元素。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>备注

专用化允许结构利用操作此类型**wchar_t**的对象的库函数。

## <a name="requirements"></a>要求

**标头：** \<string>

**命名空间：** std

## <a name="see-also"></a>请参阅

[char_traits 结构](../standard-library/char-traits-struct.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
