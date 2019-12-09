---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: fbaf9e761f9f1450ccd12dc378ab6e498aa0df08
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857874"
---
# <a name="__readdr"></a>__readdr

**Microsoft 专用**

读取指定的调试寄存器的值。

## <a name="syntax"></a>语法

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>参数

*DebugRegister*\
中用于标识调试寄存器的从0到7的常数。

## <a name="return-value"></a>返回值

指定的调试寄存器的值。

## <a name="remarks"></a>备注

这些内部函数仅在内核模式下可用，且这些例程只能用作内部函数。

## <a name="requirements"></a>需求

|内部函数|体系结构|
|---------------|------------------|
|`__readdr`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
