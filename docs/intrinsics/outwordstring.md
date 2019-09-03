---
title: __outwordstring
ms.date: 09/02/2019
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: 3cc5b0ae2101c86e3dc899b7924ec2524f0ea6e7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217119"
---
# <a name="__outwordstring"></a>__outwordstring

**Microsoft 专用**

生成指令, 该指令将从*Buffer*开始的*计数*字词发送到端口指定的 i/o 端口。 `rep outsw`

## <a name="syntax"></a>语法

```C
void __outwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>参数

*口*\
中要将数据发送到的端口。

*宽限*\
中指向要通过指定端口发送的数据的指针。

*计*\
中要发送的单词数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outwordstring`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
