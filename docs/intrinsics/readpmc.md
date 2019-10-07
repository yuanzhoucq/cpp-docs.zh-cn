---
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: af0f1874d991771423ddebfedd4624cd0b71760f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221037"
---
# <a name="__readpmc"></a>__readpmc

**Microsoft 专用**

生成指令, 该指令读取由 counter 指定的性能监视计数器。 `rdpmc`

## <a name="syntax"></a>语法

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>参数

*对抗*\
中要读取的性能计数器。

## <a name="return-value"></a>返回值

指定的性能计数器的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readpmc`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

内部函数仅在内核模式下可用, 且例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
