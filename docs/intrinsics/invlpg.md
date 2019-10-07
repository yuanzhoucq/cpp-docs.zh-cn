---
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: ba8bd81498f805992336b0dc4163fe18fa157a2c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221894"
---
# <a name="__invlpg"></a>__invlpg

**Microsoft 专用**

生成 x86 `invlpg`指令, 该指令使与按*地址*指向的内存关联的页面的翻译后备链表缓冲区 (TLB) 失效。

## <a name="syntax"></a>语法

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>参数

*地址*\
中64位地址。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__invlpg`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

内部函数`__invlpg`发出特权指令, 仅在权限级别 (CPL) 为0的内核模式下可用。

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
