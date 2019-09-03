---
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: c8df13c15b5cd8a51b77d65ad930a1852809ee30
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219238"
---
# <a name="__writecr8"></a>__writecr8

**Microsoft 专用**

将值`Data`写入 CR8 寄存器。

## <a name="syntax"></a>语法

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>参数

*数据*\
中要写入到 CR8 寄存器的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writecr8`|X64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`__writecr8`内部函数仅在内核模式下可用, 且例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
