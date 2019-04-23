---
title: _umul128
ms.date: 11/04/2016
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: afca1e62127ac2dbcfc407982dbe191d379b4acb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034960"
---
# <a name="umul128"></a>_umul128

**Microsoft 专用**

乘以作为前两个自变量传入的两个 64 位无符号整数，将产品的高 64 位置于由 `HighProduct` 指向的 64 位无符号整数，并返回产品的低 64 位。

## <a name="syntax"></a>语法

```
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

#### <a name="parameters"></a>参数

*乘数*<br/>
[in]要相乘的第一个 64 位整数。

*被乘数*<br/>
[in]要相乘的第二个 64 位整数。

*HighProduct*<br/>
[out]该产品的高 64 位。

## <a name="return-value"></a>返回值

产品的低 64 位。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_umul128`|X64|\<intrin.h>|

## <a name="example"></a>示例

```
// umul128.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_umul128)

int main()
{
    unsigned __int64 a = 0x0fffffffffffffffI64;
    unsigned __int64 b = 0xf0000000I64;
    unsigned __int64 c, d;

    d = _umul128(a, b, &c);

    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
