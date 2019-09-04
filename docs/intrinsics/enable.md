---
title: _enable
ms.date: 09/02/2019
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 7adcd4eac807b8d0937efbbe6d89f8ad6dcb157c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217870"
---
# <a name="_enable"></a>_enable

**Microsoft 专用**

启用中断。

## <a name="syntax"></a>语法

```C
void _enable(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_enable`|x86、ARM、x64、ARM64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`_enable` 指示处理器设置中断标志。 在 x86 系统上，此函数会生成“设置中断标志”(`sti`) 指令。

此函数只有在内核模式下才可用。 如果在用户模式下使用，会引发特权指令异常。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
