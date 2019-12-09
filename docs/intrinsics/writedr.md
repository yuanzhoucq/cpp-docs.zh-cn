---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 473e7223e9974d0125e772c152ea85ae90b97342
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858056"
---
# <a name="__writedr"></a>__writedr

**Microsoft 专用**

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

这些内部函数仅在内核模式下可用，且这些例程只能用作内部函数。

## <a name="requirements"></a>需求

|内部函数|体系结构|
|---------------|------------------|
|`__writedr`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
