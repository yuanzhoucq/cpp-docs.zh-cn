---
title: __ll_lshift
ms.date: 11/04/2016
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 5a91ce5db46b19be570f8d48a584a2caeabcc163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263381"
---
# <a name="lllshift"></a>__ll_lshift

**Microsoft 专用**

将按指定数目的位左移提供的 64 位值。

## <a name="syntax"></a>语法

```
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>参数

*掩码*<br/>
[in]要向左移动的 64 位整数值。

*nBit*<br/>
[in]移动的位数数。

## <a name="return-value"></a>返回值

掩码向左旋转`nBit`位。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__ll_lshift`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

如果在编译应用程序使用 64 位体系结构和`nBit`大于 63，若要移动的位数是`nBit`模 64。 如果在编译使用 32 位体系结构应用程序和`nBit`大于 31，要移动的位数是`nBit`取模 32。

`ll`名称中指示这是一个操作上`long long`(`__int64`)。

## <a name="example"></a>示例

```
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

## <a name="output"></a>Output

```
10000
```

**请注意**左的移操作没有未签名版本。 这是因为`__ll_lshift`已在使用无符号的输入的参数。 与右移位，不同的是左移，没有登录依赖性过程，因为结果中的最低有效位始终设置为零，而不考虑移动值的符号。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)