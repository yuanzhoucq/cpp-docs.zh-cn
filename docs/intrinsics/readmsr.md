---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 4398b9d42369e3a914dbec1ed2d14cafecf58483
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222336"
---
# <a name="__readmsr"></a>__readmsr

**Microsoft 专用**

生成指令, 该指令读取由`register`指定的模型特定寄存器并返回其值。 `rdmsr`

## <a name="syntax"></a>语法

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>参数

*注册*\
中要读取的特定于模型的寄存器。

## <a name="return-value"></a>返回值

指定寄存器中的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readmsr`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此函数仅在内核模式下可用, 且例程仅可用作内部函数。

有关详细信息, 请参阅 AMD 文档。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
