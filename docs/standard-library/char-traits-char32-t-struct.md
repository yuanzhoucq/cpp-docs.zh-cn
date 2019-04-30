---
title: char_traits&lt;char32_t&gt; 结构
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char_32t>
- char_traits<char32_t>
helpviewer_keywords:
- char_traits<char32_t> class
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
ms.openlocfilehash: 12fc36a9256a8a744e789fc95bb8603ee6cbf3d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379488"
---
# <a name="chartraitsltchar32tgt-struct"></a>char_traits&lt;char32_t&gt; 结构

此结构是模板结构 **char_traits\<CharType>** 对 `char32_t` 类型的一个元素的专用化。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<char32_t>;
```

## <a name="remarks"></a>备注

专用化允许结构利用库函数处理此 `char32_t` 类型的对象。

## <a name="requirements"></a>要求

**标头：** \<string>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<string>](../standard-library/string.md)<br/>
[char_traits 结构](../standard-library/char-traits-struct.md)<br/>
