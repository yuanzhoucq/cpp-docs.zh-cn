---
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 988284b81c9f04ee5d7f09f8a2f173a689f9fb55
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230514"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Microsoft 专用**

将提供的64位值向左移动指定的位数。

## <a name="syntax"></a>语法

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>参数

*掩盖*\
中要向左移动的64位整数值。

*nBit*\
中要移位的位数。

## <a name="return-value"></a>返回值

按位向左移动的掩码 `nBit` 。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`__ll_lshift`|x86、x64|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

如果为64位体系结构编译程序，并且大于 `nBit` 63，则要移位的位数为 `nBit` 模数64。 如果为32位体系结构编译程序，并且大于 `nBit` 31，则要移位的位数为 `nBit` 模数32。

`ll`名称中的指示它是对（）的操作 **`long long`** **`__int64`** 。

## <a name="example"></a>示例

```cpp
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>输出

```Output
10000
```

> [!NOTE]
> 左移操作没有未签名的版本。 这是因为 `__ll_lshift` 已使用未签名的输入参数。 与右移位不同，左移不会有任何符号相关性，因为结果中的最小有效位始终设置为零，而不考虑值的符号。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
