---
title: __getcallerseflags
ms.date: 09/02/2019
f1_keywords:
- _getcallerseflags
- _getcallerseflags_cpp
helpviewer_keywords:
- _getcallerseflags intrinsic
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
ms.openlocfilehash: d6279db10ec38da7482b26e19e31f2d34dd48a07
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222164"
---
# <a name="__getcallerseflags"></a>__getcallerseflags

**Microsoft 专用**

从调用方的上下文返回 EFLAGS 值。

## <a name="syntax"></a>语法

```C
unsigned int __getcallerseflags(void);
```

## <a name="return-value"></a>返回值

来自调用方的上下文的 EFLAGS 值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__getcallerseflags`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

## <a name="example"></a>示例

```cpp
// getcallerseflags.cpp
// processor: x86, x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__getcallerseflags)

unsigned int g()
{
    unsigned int EFLAGS = __getcallerseflags();
    printf_s("EFLAGS 0x%x\n", EFLAGS);
    return EFLAGS;
}
unsigned int f()
{
    return g();
}

int main()
{
    unsigned int i;
    i = f();
    i = g();
    return 0;
}
```

```Output
EFLAGS 0x202
EFLAGS 0x206
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
