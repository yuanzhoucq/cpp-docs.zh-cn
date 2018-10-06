---
title: __lidt |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f07f4aee87df98b93c5aca54d1435339bf546539
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820654"
---
# <a name="lidt"></a>__lidt

**Microsoft 专用**

加载指定的内存位置中的值的中断描述符表寄存器 (IDTR)。

## <a name="syntax"></a>语法

```
void __lidt(void * Source);
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Source*|[in]指向要复制到 IDTR 的值。|

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__lidt`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`__lidt`函数等同于`LIDT`机器指令，并且仅在内核模式下可用。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，2 卷： 指令集引用"在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)