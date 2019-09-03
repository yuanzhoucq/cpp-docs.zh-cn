---
title: __stosd
ms.date: 09/02/2019
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: c46bb124390ff23d79361c66530493c48faf3f0a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219976"
---
# <a name="__stosd"></a>__stosd

**Microsoft 专用**

生成存储字符串指令 (`rep stosd`)。

## <a name="syntax"></a>语法

```C
void __stosd(
   unsigned long* Destination,
   unsigned long Data,
   size_t Count
);
```

### <a name="parameters"></a>参数

*位置*\
弄操作的目标。

*数据*\
中要存储的数据。

*计*\
中要写入的双字块的长度。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__stosd`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

结果是, 将双字*数据*写入到*目标*所指向的内存位置上的*计数*的双字块中。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```C
// stosd.c
// processor: x86, x64

#include <stdio.h>
#include <memory.h>
#include <intrin.h>

#pragma intrinsic(__stosd)

int main()
{
    unsigned long val = 99999;
    unsigned long a[10];

    memset(a, 0, sizeof(a));
    __stosd(a+1, val, 2);

printf_s( "%u %u %u %u",
              a[0], a[1], a[2], a[3]);
}
```

```Output
0 99999 99999 0
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
