---
title: __readcr2 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr2
dev_langs:
- C++
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c22c16d746c869673783c65cf24aa1d6d95eb61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442274"
---
# <a name="readcr2"></a>__readcr2

**Microsoft 专用**

读取 CR2 寄存器并返回其值。

## <a name="syntax"></a>语法

```
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>返回值

CR2 寄存器中的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readcr2`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数只在内核模式下可用，例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)