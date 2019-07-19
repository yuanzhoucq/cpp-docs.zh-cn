---
title: '&lt;cstdalign&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdalign>
- cstdalign
- __alignas_is_defined
- __alignof_is_defined
helpviewer_keywords:
- cstdalign header
- __alignas_is_defined
- __alignof_is_defined
ms.assetid: 9d570924-d299-4225-9a58-8c4c820f5903
ms.openlocfilehash: 603a590190c50495aa80f1b41a574149eb8f760a
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342836"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign&gt;

在某些C++标准库实现中, 此标头包括 C 标准库\<标头 stdalign >, 并将`std`关联名称添加到命名空间。 由于未在 MSVC 中实现该标头\<, 因此 cstdalign > 标头`__alignas_is_defined`定义`__alignof_is_defined`兼容性宏和。

> [!NOTE]
> 由于 stdalign > 标头定义了作为关键字的宏C++, 其中包括不起作用。 \< 中\< C++弃用了 stdalign > 标头。 \<Cstdalign > 标头在 c + + 17 中已弃用, 并已在草案 c + + 20 标准中删除。

## <a name="requirements"></a>要求

**标头:** \<cstdalign >

**命名空间：** std

## <a name="macros"></a>宏

| 宏 | 描述 |
| - | - |
| `__alignas_is_defined` | 可扩展到整数常数1的 C 兼容性宏。 |
| `__alignof_is_defined` | 可扩展到整数常数1的 C 兼容性宏。 |

## <a name="see-also"></a>请参阅

[标头文件引用](cpp-standard-library-header-files.md)\
[C++标准库概述](cpp-standard-library-overview.md)\
[标准库中的C++线程安全](thread-safety-in-the-cpp-standard-library.md)
