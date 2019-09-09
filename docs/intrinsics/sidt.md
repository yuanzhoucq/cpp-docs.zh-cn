---
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: d6b685da0e02373307a3149c5b7b28213f37ad40
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222323"
---
# <a name="__sidt"></a>__sidt

**Microsoft 专用**

将中断描述符表寄存器（IDTR）的值存储在指定的内存位置。

## <a name="syntax"></a>语法

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>参数

*位置*\
中指向存储 IDTR 的内存位置的指针。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__sidt`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`__sidt` 函数等同于 `SIDT` 计算机指令。 有关详细信息，请搜索文档 "Intel 体系结构软件开发人员手册，第2卷：说明集[参考 "。](https://software.intel.com/articles/intel-sdm)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
