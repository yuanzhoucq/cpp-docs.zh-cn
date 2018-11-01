---
title: __umulh
ms.date: 11/04/2016
f1_keywords:
- __umulh
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
ms.openlocfilehash: b116de7cd91d26463858fb03e5f319e2a2da1cde
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524795"
---
# <a name="umulh"></a>__umulh

**Microsoft 专用**

返回两个 64 位无符号整数的产品的高 64 位。

## <a name="syntax"></a>语法

```
unsigned __int64 __umulh( 
   unsigned __int64 a, 
   unsigned __int64 b 
);
```

#### <a name="parameters"></a>参数

*a*<br/>
[in]要相乘的第一个数字。

*b*<br/>
[in]要相乘的第二个数字。

## <a name="return-value"></a>返回值

128 位乘法运算结果的高 64 位。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__umulh`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

这些例程只能用作内部函数。

## <a name="example"></a>示例

```
// umulh.cpp
// processor: X64
#include <cstdio>
#include <intrin.h>

int main()
{
    unsigned __int64 i = 0x10;
    unsigned __int64 j = 0xFEDCBA9876543210;
    unsigned __int64 k = i * j; // k has the low 64 bits
                                // of the product.
    unsigned __int64 result;
    result = __umulh(i, j); // result has the high 64 bits
                            // of the product.
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);
    return 0;
}
```

```Output
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)