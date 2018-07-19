---
title: char_traits&lt;wchar_t&gt; 结构 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d8b87b51bfeef68ef8bfe22c8e7e201929aa3f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957069"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 结构

专用化的模板结构的类**char_traits\<CharType >** 类型的元素**wchar_t**。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>备注

专用化允许结构利用库函数处理此类型的对象**wchar_t**。

## <a name="requirements"></a>要求

**标头：** \<string>

**命名空间：** std

## <a name="see-also"></a>请参阅

[char_traits 结构](../standard-library/char-traits-struct.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
