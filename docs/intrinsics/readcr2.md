---
title: __readcr2
ms.date: 09/02/2019
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: 482f4548a692d6aa3b65fbc42caabda29bb393c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217108"
---
# <a name="__readcr2"></a>__readcr2

**Microsoft 专用**

读取 CR2 注册并返回其值。

## <a name="syntax"></a>语法

```C
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>返回值

CR2 寄存器中的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readcr2`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

内部函数仅在内核模式下可用, 且例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
