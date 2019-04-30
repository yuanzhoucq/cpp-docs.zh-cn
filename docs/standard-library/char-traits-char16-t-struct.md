---
title: char_traits&lt;char16_t&gt; 结构
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: def0023b259a7b4816bdda29684c1dd9853d5f5b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379527"
---
# <a name="chartraitsltchar16tgt-struct"></a>char_traits&lt;char16_t&gt; 结构

此结构是模板结构 **char_traits\<CharType>** 对 `char16_t` 类型的一个元素的专用化。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>备注

专用化允许结构利用库函数处理 `char16_t` 类型的对象。

## <a name="requirements"></a>要求

**标头：** \<string>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<string>](../standard-library/string.md)<br/>
[char_traits 结构](../standard-library/char-traits-struct.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
