---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 2ab94a44d08165ca6e8f394278e24d7c8d201398
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223494"
---
# <a name="__unaligned"></a>__unaligned

**特定于 Microsoft 的**。 当你使用修饰符声明指针时 **`__unaligned`** ，编译器将假定指针寻址未对齐的数据。 因此，生成了平台相应的代码来处理通过指针进行的未对齐读写操作。

## <a name="remarks"></a>备注

此修饰符描述由指针寻址的数据的对齐方式;指针本身被假定为对齐。

关键字的必要性 **`__unaligned`** 因平台和环境而异。 如果未能适当地标记数据，可能会导致问题，范围从性能损失到硬件故障。 **`__unaligned`** 修饰符对于 x86 平台无效。

对于与以前版本的兼容性，为， **`_unaligned`** **`__unaligned`** 除非指定编译器选项 " [ `/Za` \( 禁用语言扩展](../build/reference/za-ze-disable-language-extensions.md)"，否则将是同义词。

有关对齐的详细信息，请参阅：

- [`align`](../cpp/align-cpp.md)

- [`alignof`操作员](../cpp/alignof-operator.md)

- [`pack`](../preprocessor/pack.md)

- [`/Zp`（结构成员对齐）](../build/reference/zp-struct-member-alignment.md)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
