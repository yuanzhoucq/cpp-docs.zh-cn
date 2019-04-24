---
title: __faststorefence
ms.date: 11/04/2016
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: a0c8027f443a475b03521920e2e036e7ed4eaafb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036690"
---
# <a name="faststorefence"></a>__faststorefence

**Microsoft 专用**

保证每个以前的内存引用（包括加载和存储内存引用）在任何后续的内存引用之前全局可见。

## <a name="syntax"></a>语法

```
void __faststorefence();
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__faststorefence`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

生成完整的内存屏障指令序列，以保证在此内部函数之前发出的加载和存储操作在执行继续之前全局可见。 效果相当于所有 x64 平台上的 `_mm_mfence` 内部函数，但是速度更快。

在 AMD64 平台上，此例程会生成一个指令，该指令是比 `sfence` 指令更快的存储隔离。 对于时间关键型代码，仅在 AMD64 平台上使用此内部函数而不是 `_mm_sfence`。 在 Intel x64 平台上，`_mm_sfence` 指令速度更快。

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)