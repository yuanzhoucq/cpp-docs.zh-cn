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
ms.openlocfilehash: 158ecbf39320d70b51f1f498a0b689ba58fec363
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221822"
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

按`nBit`位向左移动的掩码。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__ll_lshift`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

如果为64位体系结构编译程序, 并且`nBit`大于 63, 则要移位的位数为`nBit`模数64。 如果为32位体系结构编译程序, 并且`nBit`大于 31, 则要移位的位数为`nBit`模数32。

名称`ll`中的指示它是对`long long` (`__int64`) 的操作。

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

## <a name="output"></a>Output

```Output
10000
```

> [!NOTE]
> 左移操作没有未签名的版本。 这是因为`__ll_lshift`已使用未签名的输入参数。 与右移位不同, 左移不会有任何符号相关性, 因为结果中的最小有效位始终设置为零, 而不考虑值的符号。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
