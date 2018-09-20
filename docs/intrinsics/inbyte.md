---
title: __inbyte |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inbyte
- __inbyte_cpp
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e9b4950c16cdab8dd282f772e84f7f222246328
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414454"
---
# <a name="inbyte"></a>__inbyte

**Microsoft 专用**

将生成`in`指令，返回一个字节读取由指定的端口`Port`。

## <a name="syntax"></a>语法

```
unsigned char __inbyte(
   unsigned short Port
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要读取的端口。

## <a name="return-value"></a>返回值

从指定的端口读取的字节。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__inbyte`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)