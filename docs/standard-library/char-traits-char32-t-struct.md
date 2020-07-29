---
title: char_traits&lt;char32_t&gt; 结构
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char_32t>
- char_traits<char32_t>
helpviewer_keywords:
- char_traits<char32_t> class
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
ms.openlocfilehash: 0daf61f641b0b68bf806bba081b3c312777c6fe7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230202"
---
# <a name="char_traitsltchar32_tgt-struct"></a>char_traits&lt;char32_t&gt; 结构

作为模板结构的专用化的结构，该**结构 \<CharType> char_traits**类型为的元素 **`char32_t`** 。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<char32_t>;
```

## <a name="remarks"></a>备注

专用化允许结构利用操作此类型对象的库函数 **`char32_t`** 。

## <a name="requirements"></a>要求

**标头：**\<string>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[\<string>](../standard-library/string.md)\
[char_traits 结构](../standard-library/char-traits-struct.md)
