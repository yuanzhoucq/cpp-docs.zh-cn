---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: cfb6e5a11bed5feec3435ab604d22b8f532d3400
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217525"
---
# <a name="__inword"></a>__inword

**Microsoft 专用**

使用`in`指令从指定端口读取数据。

## <a name="syntax"></a>语法

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>参数

*口*\
中要从其读取的端口。

## <a name="return-value"></a>返回值

读取的数据的单词。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__inword`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
