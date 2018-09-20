---
title: __int2c | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __int2c
- __int2c_cpp
dev_langs:
- C++
helpviewer_keywords:
- int2c intrinsic
- int 2c instruction
- __int2c intrinsic
ms.assetid: aa20ff30-adef-42bb-8577-8010f3122f8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcb8859f00724eb7865198c662850a60314ffdc3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419979"
---
# <a name="int2c"></a>__int2c

**Microsoft 专用**

将生成`int 2c`指令，这会触发`2c`中断。

## <a name="syntax"></a>语法

```
void __int2c(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__int2c`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)