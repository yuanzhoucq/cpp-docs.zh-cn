---
title: __wbinvd |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __wbinvd
dev_langs:
- C++
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1f412de7c8752ba1c1ba1324d20e1d4fb4c6a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388376"
---
# <a name="wbinvd"></a>__wbinvd

**Microsoft 专用**

生成的写回和使之无效的缓存 (`wbinvd`) 指令。

## <a name="syntax"></a>语法

```
void __wbinvd(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__wbinvd`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此函数选项仅适用于内核模式权限级别 (CPL) 为 0，且该例程仅用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)