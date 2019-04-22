---
title: __halt
ms.date: 11/04/2016
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: dd68c88a13035ca25f89304bcd84267a73978420
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025946"
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

`__halt`函数等同于`HLT`机器指令，并且仅在内核模式下可用。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，卷 2:指令设置参考，"在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)