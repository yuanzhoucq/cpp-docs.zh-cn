---
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: f0036763ed7315a54fbfe6dcc873b46b52f0730c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222142"
---
# <a name="__inbyte"></a>__inbyte

**Microsoft 专用**

生成指令, 并返回从`Port`指定的端口读取的单个字节。 `in`

## <a name="syntax"></a>语法

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>参数

*口*\
中要从其读取的端口。

## <a name="return-value"></a>返回值

从指定端口中读取的字节。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__inbyte`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
