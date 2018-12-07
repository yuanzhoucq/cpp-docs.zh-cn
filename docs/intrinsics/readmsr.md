---
title: __readmsr
ms.date: 11/04/2016
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 891ca43af4a81b63de39d367ea418e43811f78d0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326402"
---
# <a name="readmsr"></a>__readmsr

**Microsoft 专用**

将生成`rdmsr`指令，读取指定的模型特定寄存器`register`并返回其值。

## <a name="syntax"></a>语法

```
__int64 __readmsr(
   int register
);
```

#### <a name="parameters"></a>参数

*register*<br/>
[in]读取模型特定寄存器。

## <a name="return-value"></a>返回值

中指定的寄存器的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readmsr`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此函数仅在内核模式下可用，例程仅可用作内部函数。

有关详细信息，请参阅 AMD 文档。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)