---
title: __writecr3
ms.date: 09/02/2019
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: f2472a21fe42f10dbf0918480ef02f7e48109747
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219274"
---
# <a name="__writecr3"></a>__writecr3

**Microsoft 专用**

将值`Data`写入 CR3 寄存器。

## <a name="syntax"></a>语法

```C
void writecr3(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>参数

*数据*\
中要写入到 CR3 寄存器的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writecr3`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此内部函数只在内核模式下可用，例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
