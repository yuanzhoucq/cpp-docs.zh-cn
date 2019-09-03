---
title: __readcr4
ms.date: 09/02/2019
f1_keywords:
- __readcr4
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
ms.openlocfilehash: 4d43b5204d412de40284f89cfd4d74f1c1f9d86d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216733"
---
# <a name="__readcr4"></a>__readcr4

**Microsoft 专用**

读取 CR4 注册并返回其值。

## <a name="syntax"></a>语法

```C
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>返回值

CR4 寄存器中的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readcr4`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

内部函数仅在内核模式下可用, 且例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
