---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 24778b761ada56830b155a2fc65e90f54ba729ed
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217506"
---
# <a name="__lidt"></a>__lidt

**Microsoft 专用**

用指定内存位置中的值加载中断描述符表 register （IDTR）。

## <a name="syntax"></a>语法

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*源*|中指向要复制到 IDTR 的值的指针。|

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__lidt`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`__lidt`函数等效`LIDT`于计算机指令，仅在内核模式下可用。 有关详细信息，请搜索文档 "Intel 体系结构软件开发人员手册，第2卷：说明集[参考 "。](https://software.intel.com/articles/intel-sdm)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
