---
title: __readcr0
ms.date: 09/02/2019
f1_keywords:
- __readcr0
helpviewer_keywords:
- __readcr0 intrinsic
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
ms.openlocfilehash: 8f3abc7177fa2e648c02eab498d04bcada96bb06
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221280"
---
# <a name="__readcr0"></a>__readcr0

**Microsoft 专用**

读取 CR0 寄存器并返回其值。

## <a name="syntax"></a>语法

```C
unsigned long __readcr0(void);  /* X86 */
unsigned __int64 __readcr0(void);  /* X64 */
```

## <a name="return-value"></a>返回值

CR0 寄存器中的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readcr0`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

内部函数仅在内核模式下可用, 且例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
