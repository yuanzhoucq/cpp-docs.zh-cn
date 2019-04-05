---
title: __sidt
ms.date: 11/04/2016
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: 88dbb4713577fcf224e1c5646bf4c38b2a1dfafe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036755"
---
# <a name="sidt"></a>__sidt

**Microsoft 专用**

将存储在指定的内存位置中断描述符表寄存器 (IDTR) 的值。

## <a name="syntax"></a>语法

```
void __sidt(void * Destination);
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*目标*|[in]指向存储 IDTR 的内存位置的指针。|

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__sidt`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`__sidt` 函数等同于 `SIDT` 计算机指令。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，卷 2:指令设置参考，"在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__lidt](../intrinsics/lidt.md)