---
title: __readcr8
ms.date: 11/04/2016
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: d4c0b22d38d725566062d2da98839579c22d571c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036859"
---
# <a name="readcr8"></a>__readcr8

**Microsoft 专用**

读取 CR8 寄存器并返回其值。

## <a name="syntax"></a>语法

```
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>返回值

CR8 寄存器中的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readcr8`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数只在内核模式下可用，例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)