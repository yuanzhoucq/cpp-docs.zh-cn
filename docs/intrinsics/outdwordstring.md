---
title: __outdwordstring
ms.date: 09/02/2019
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 50908a65795af617f18a497c073cfefe009dfd80
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217161"
---
# <a name="__outdwordstring"></a>__outdwordstring

**Microsoft 专用**

生成指令, 该指令从`Count`指定的`Port`i/o `Buffer`端口开始发送双字。 `rep outsd`

## <a name="syntax"></a>语法

```C
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>参数

*口*\
中要将数据发送到的端口。

*宽限*\
中指向要通过指定端口发送的数据的指针。

*计*\
中要发送的双字的数目。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outdwordstring`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
