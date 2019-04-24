---
title: __lidt
ms.date: 11/04/2016
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 757309603af48820a17668cfe272bbeaad9239b3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038468"
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
|*源*|[in]指向要复制到 IDTR 的值。|

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__lidt`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`__lidt`函数等同于`LIDT`机器指令，并且仅在内核模式下可用。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，卷 2:指令设置参考，"在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)