---
title: __getcallerseflags |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _getcallerseflags
- _getcallerseflags_cpp
dev_langs:
- C++
helpviewer_keywords:
- _getcallerseflags intrinsic
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f16079fce7bda86a376baf783db8b05ec098015
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410190"
---
# <a name="getcallerseflags"></a>__getcallerseflags

**Microsoft 专用**

从调用方的上下文返回 EFLAGS 值。

## <a name="syntax"></a>语法

```
unsigned int __getcallerseflags(void);
```

## <a name="return-value"></a>返回值

从调用方的上下文 EFLAGS 值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__getcallerseflags`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
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