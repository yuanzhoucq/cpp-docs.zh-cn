---
title: __segmentlimit
ms.date: 11/04/2016
f1_keywords:
- __segmentlimit
helpviewer_keywords:
- __segmentlimit intrinsic
- lsl instruction
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
ms.openlocfilehash: 854e3efce48b7ed863db1a94467a6da99d796a89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636418"
---
# <a name="segmentlimit"></a>__segmentlimit

**Microsoft 专用**

生成`lsl`（负载段限制） 指令。

## <a name="syntax"></a>语法

```
unsigned long __segmentlimit( 
   unsigned long a 
);
```

#### <a name="parameters"></a>参数

*a*<br/>
[in]一个常量，它指定段选择器。

## <a name="return-value"></a>返回值

指定的段选择器的段限制`a`，前提是选择器在当前的权限级别是有效的并且可见。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__segmentlimit`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

如果不能检索段限制，此指令将失败。 在失败时，此指令清除 ZF 标志和返回值未定义。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
#include <stdio.h>

#ifdef _M_IX86
typedef unsigned int READETYPE;
#else
typedef unsigned __int64 READETYPE;
#endif

#define EFLAGS_ZF      0x00000040
#define KGDT_R3_DATA    0x0020
#define RPL_MASK        0x3

extern "C"
{
unsigned long __segmentlimit (unsigned long);
READETYPE __readeflags();
}

#pragma intrinsic(__readeflags)
#pragma intrinsic(__segmentlimit)

int main(void)
{
   const unsigned long initsl = 0xbaadbabe;
   READETYPE eflags = 0;
   unsigned long sl = initsl;

   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);

   eflags = __readeflags();

   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");

   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");

   // You can verify the value of sl to make sure that the instruction wrote to it
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");

   return 0;
}
```

```Output
Before: segment limit =0xbaadbabe eflags =0x0
After: segment limit =0xffffffff eflags =0x256 eflags.zf = set
Success!
sl was changed
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)