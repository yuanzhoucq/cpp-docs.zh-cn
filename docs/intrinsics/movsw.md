---
title: __movsw
ms.date: 09/02/2019
f1_keywords:
- __movsw
helpviewer_keywords:
- movsw instruction
- rep movsw instruction
- __movsw intrinsic
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
ms.openlocfilehash: 67eef7fe0a5b9803650f345740a8c40262cd2014
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221722"
---
# <a name="__movsw"></a>__movsw

**Microsoft 专用**

生成 Move String (`rep movsw`) 指令。

## <a name="syntax"></a>语法

```C
void __movsw(
   unsigned short* Destination,
   unsigned short* Source,
   size_t Count
);
```

### <a name="parameters"></a>参数

*位置*\
弄操作的目标。

*Source*\
中操作的源。

*计*\
中要复制的单词数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__movsw`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

结果就是将*源*指向的第一个*计数*词复制到*目标*字符串。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```cpp
// movsw.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsw)

int main()
{
    unsigned short s1[10];
    unsigned short s2[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    __movsw(s1, s2, 10);

    for (int i = 0; i < 10; i++)
        printf_s("%d ", s1[i]);
    printf_s("\n");
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
