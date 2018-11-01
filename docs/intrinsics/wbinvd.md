---
title: __wbinvd
ms.date: 11/04/2016
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: 0f775ba94c2dee1c2568e66b09fa1ffb31f512bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482532"
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