---
title: __ull_rshift
ms.date: 11/04/2016
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: 5d62ec1526aff595c14a53e9eca43a7a3118c8fa
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034519"
---
# <a name="ullrshift"></a>__ull_rshift

**Microsoft 专用**

在 x64 上，第二个参数指定的位数右移由右侧的第一个参数指定的 64 位值。

## <a name="syntax"></a>语法

```
unsigned __int64 __ull_rshift(
   unsigned __int64 mask, 
   int nBit
);
```

#### <a name="parameters"></a>参数

*掩码*<br/>
[in]要右移位的 64 位整数值。

*nBit*<br/>
[in]要切换，请取模 x86 上的 32 和取模运算在 x64 上的 64 位的数。

## <a name="return-value"></a>返回值

掩码移动`nBit`位。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__ull_rshift`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

如果第二个参数大于 31 x86 (63 在 x64 上) 上，该数字执行取模 32 (64 在 x64 上) 若要确定移动的位数编号。 `ull`名称中指示`unsigned long long (unsigned __int64)`。

## <a name="example"></a>示例

```
// ull_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ull_rshift)

int main()
{
   unsigned __int64 mask = 0x100;
   int nBit = 8;
   mask = __ull_rshift(mask, nBit);
   cout << hex << mask << endl;
}
```

## <a name="output"></a>Output

```
1
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)