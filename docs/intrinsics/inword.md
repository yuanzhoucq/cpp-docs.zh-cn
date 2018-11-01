---
title: __inword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 85498fd85f5401ad123794cc9aaed2b278db867c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475356"
---
# <a name="inword"></a>__inword

**Microsoft 专用**

从指定的端口使用读取数据`in`指令。

## <a name="syntax"></a>语法

```
unsigned short __inword(
   unsigned short Port
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要读取的端口。

## <a name="return-value"></a>返回值

读取的数据的单词。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__inword`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)