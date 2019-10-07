---
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: 66f5e05e7673523966ef35ac743fc585930b511c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222159"
---
# <a name="__halt"></a>__halt

**Microsoft 专用**

暂停微处理器，直到启用了中断、不可屏蔽中断（NMI）或重置。

## <a name="syntax"></a>语法

```C
void __halt( void );
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__halt`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`__halt`函数等效`HLT`于计算机指令，仅在内核模式下可用。 有关详细信息，请搜索文档 "Intel 体系结构软件开发人员手册，第2卷：说明集[参考 "。](https://software.intel.com/articles/intel-sdm)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
