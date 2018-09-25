---
title: __halt |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __halt
- __halt_cpp
dev_langs:
- C++
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d833d1e62cb2df94d6cad740aa6e1513d55d5ecf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431042"
---
# <a name="halt"></a>__halt

**Microsoft 专用**

已启用的中断、 不可屏蔽的中断 (NMI) 或重置发生之前就会停止微处理器。

## <a name="syntax"></a>语法

```
void __halt( void );
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__halt`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`__halt`函数等同于`HLT`机器指令，并且仅在内核模式下可用。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，2 卷： 指令集引用"在[Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm)站点。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)