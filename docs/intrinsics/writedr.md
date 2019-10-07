---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 715ef7432d506c2758c9c3da913e9c0ebb24e13f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219220"
---
# <a name="__writedr"></a>__writedr

将指定的值写入指定的调试寄存器。

## <a name="syntax"></a>语法

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>参数

*DebugRegister*\
中标识调试寄存器的从0到7的数字。

*DebugValue*\
中要写入调试寄存器的值。

## <a name="remarks"></a>备注

这些内部函数仅在内核模式下可用, 且这些例程只能用作内部函数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writedr`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
