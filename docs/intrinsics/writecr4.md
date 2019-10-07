---
title: __writecr4
ms.date: 09/02/2019
f1_keywords:
- _writecr4
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
ms.openlocfilehash: 1afdadcdfdbf1060c87e3865dd5597b0b9a2ea6b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219265"
---
# <a name="__writecr4"></a>__writecr4

**Microsoft 专用**

将值`Data`写入 CR4 寄存器。

## <a name="syntax"></a>语法

```C
void writecr4(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>参数

*数据*\
中要写入到 CR4 寄存器的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writecr4`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此内部函数只在内核模式下可用，例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
