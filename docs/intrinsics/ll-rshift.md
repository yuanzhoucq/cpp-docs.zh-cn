---
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: ad17991d84acb7e531baf9435610ebd566197a22
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217497"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Microsoft 专用**

将第一个参数指定的64位值向右移位, 由第二个参数指定的位数。

## <a name="syntax"></a>语法

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>参数

*掩盖*\
中要右移的64位整数值。

*nBit*\
中在 x86 上要移位的位数、x64 上的取64和取模32。

## <a name="return-value"></a>返回值

按`nBit`位移动的掩码。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__ll_rshift`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

如果第二个参数大于 x64 上的 64 (x86 上为 32), 则将该数字取模 64 (x86 上的 32) 以确定要移位的位数。 前缀指示它是对`long long`的操作, 另一个名称为`__int64`64 位有符号整数类型。 `ll`

## <a name="example"></a>示例

```cpp
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>Output

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> 如果`_ull_rshift`使用了, 则右移后的值的 MSB 将为零, 因此在负值情况下不会获得所需的结果。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
