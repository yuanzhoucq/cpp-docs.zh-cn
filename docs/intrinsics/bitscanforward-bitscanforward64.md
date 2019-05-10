---
title: _BitScanForward、_BitScanForward64
ms.date: 11/04/2016
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
ms.openlocfilehash: 8b09aeee485611ddd20d51b4c1e36ec98c03c26e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264206"
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward、_BitScanForward64

**Microsoft 专用**

从设置位 (1) 的最低有效位 (LSB) 到最高有效位 (MSB) 搜索掩码数据。

## <a name="syntax"></a>语法

```
unsigned char _BitScanForward(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanForward64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

#### <a name="parameters"></a>参数

*Tuple*<br/>
[out]使用找到的第一个设置位 (1) 的位位置加载。

*掩码*<br/>
[in]要搜索的 32 位或 64 位值。

## <a name="return-value"></a>返回值

如果掩码为零，则为 0；否则为非零值。

## <a name="remarks"></a>备注

如果找到一个设置位，则将在第一个参数中返回已找到的第一个设置位的位位置。 如果没有发现任何设置位，则返回 0；否则返回 1。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_BitScanForward`|x86、 ARM、 x64|
|`_BitScanForward64`|ARM、 x64|

**标头文件** \<intrin.h >

## <a name="example"></a>示例

```
// BitScanForward.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanForward)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanForward(&index, mask);
   if (isNonzero)
   {
      cout << "Mask: " << mask << " Index: " << index << endl;
   }
   else
   {
      cout << "No set bits found.  Mask is zero." << endl;
   }
}
```

## <a name="input"></a>输入

```
12
```

## <a name="sample-output"></a>示例输出

```
Enter a positive integer as the mask:
Mask: 12 Index: 2
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)