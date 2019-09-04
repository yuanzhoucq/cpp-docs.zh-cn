---
title: __movsq
ms.date: 09/02/2019
f1_keywords:
- __movsq
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
ms.openlocfilehash: 66de1971c48f6697fd06579fac635cce31545e92
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217258"
---
# <a name="__movsq"></a>__movsq

**Microsoft 专用**

生成重复的 Move String (`rep movsq`) 指令。

## <a name="syntax"></a>语法

```C
void __movsq(
   unsigned char* Destination,
   unsigned char* Source,
   size_t Count
);
```

### <a name="parameters"></a>参数

*位置*\
弄操作的目标。

*Source*\
中操作的源。

*计*\
中要复制的 quadwords 的数目。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__movsq`|X64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

结果是将*源*指向的第一个*计数*quadwords 复制到*目标*字符串。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```cpp
// movsq.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsq)

int main()
{
    unsigned __int64 a1[10];
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,
                               150, 50};
    __movsq(a1, a2, 10);

    for (int i = 0; i < 10; i++)
       printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
