---
title: __wbinvd
ms.date: 11/04/2016
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: 99c7a452e063dea328e4aa1362aae8783929deb0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390017"
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