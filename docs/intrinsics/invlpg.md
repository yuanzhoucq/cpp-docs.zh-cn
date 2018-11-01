---
title: __invlpg
ms.date: 11/04/2016
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: 0ff46aa15fbb8728ce02255209a32f01a168609b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629380"
---
# <a name="invlpg"></a>__invlpg

**Microsoft 专用**

生成 x86`invlpg`指令，这会转换旁路缓冲器 (TLB) 使指向的内存与关联的页为`Address`。

## <a name="syntax"></a>语法

```
void __invlpg(
   void* Address
);
```

#### <a name="parameters"></a>参数

*地址*<br/>
[in]一个 64 位地址。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__invlpg`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

内部函数`__invlpg`发出特权的指令和选项仅适用于内核模式权限级别 (CPL) 为 0。

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)