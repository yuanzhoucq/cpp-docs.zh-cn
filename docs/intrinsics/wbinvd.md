---
title: __wbinvd
ms.date: 09/02/2019
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: fe888ef578f0c2e077911537d401890b63372a0b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219383"
---
# <a name="__wbinvd"></a>__wbinvd

**Microsoft 专用**

生成写回并使 Cache (`wbinvd`) 指令无效。

## <a name="syntax"></a>语法

```C
void __wbinvd(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__wbinvd`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此函数仅适用于具有0权限级别 (CPL) 的内核模式, 并且例程只能作为内部函数使用。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
