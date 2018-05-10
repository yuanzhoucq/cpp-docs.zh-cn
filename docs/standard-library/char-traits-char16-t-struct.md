---
title: char_traits&lt;char16_t&gt;结构 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24d6c3d5dd11290ce4151b5d54885ba492b8ee45
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
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
