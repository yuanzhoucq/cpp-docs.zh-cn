---
title: '&lt;random&gt; 函数'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78873930"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函数

## <a name="generate_canonical"></a>generate_canonical

从随机序列返回浮点值。

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>parameters

*RealType*\
浮点整型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

*Bits*\
要使用的随机性位数。

*生成器*\
随机数生成器类。

*Gen*\
对类型*生成器*的随机数生成器的实例的引用。

### <a name="remarks"></a>备注

模板函数重复调用*Gen* `operator()`，并将返回的值打包为类型为*RealType*的浮点值 `x`，直到它在 `x`中收集了指定数目的尾数位。 指定的数字是*位*（必须为非零）和*RealType*中的尾数位的最小值。 第一个调用提供最低序位。 该函数返回 `x`。
