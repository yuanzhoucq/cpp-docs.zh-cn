---
title: __writedr
ms.date: 11/04/2016
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: f8049485d40185d83ed01c91ad336e83f3e79834
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651810"
---
# <a name="writedr"></a>__writedr

将指定的值写入到指定的调试注册。

## <a name="syntax"></a>语法

```
void __writedr(unsigned DebugRegister, unsigned DebugValue);
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);
```

#### <a name="parameters"></a>参数

*DebugRegister*<br/>
[in]一个介于 0 到 7 标识调试注册。

*DebugValue*<br/>
[in]一个值，以写入调试注册。

## <a name="remarks"></a>备注

这些内部函数仅在内核模式中可用，例程只能用作内部函数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writedr`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__readdr](../intrinsics/readdr.md)