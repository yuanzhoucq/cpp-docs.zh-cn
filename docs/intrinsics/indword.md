---
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 790b65c8a565124df92b82b7ea17174788086a96
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222114"
---
# <a name="__indword"></a>__indword

**Microsoft 专用**

使用`in`指令从指定端口读取一个双字数据。

## <a name="syntax"></a>语法

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>参数

*口*\
中要从其读取的端口。

## <a name="return-value"></a>返回值

从端口读取的字词。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__indword`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
