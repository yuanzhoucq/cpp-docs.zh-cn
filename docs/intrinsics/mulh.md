---
title: __mulh |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __mulh
dev_langs:
- C++
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9393026814e8f3f7dd90704cd08ea96dfb9a35a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407317"
---
# <a name="mulh"></a>__mulh

**Microsoft 专用**

返回两个 64 位有符号整数的产品的高 64 位。

## <a name="syntax"></a>语法

```
__int64 __mulh( 
   __int64 a, 
   __int64 b 
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
|`__mulh`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
// mulh.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__mulh)

int main()
{
    __int64 a = 0x0fffffffffffffffI64;
    __int64 b = 0xf0000000I64;

    __int64 result = __mulh(a, b); // the high 64 bits
    __int64 result2 = a * b; // the low 64 bits

    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",
             a, b, result, result2);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)