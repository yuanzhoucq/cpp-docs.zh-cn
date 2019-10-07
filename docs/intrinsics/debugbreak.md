---
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: e4cf2c85818a878417c560ddb5a80f8690e60a93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217922"
---
# <a name="__debugbreak"></a>__debugbreak

**Microsoft 专用**

将在代码中引起断点，并在其中提示用户运行调试程序。

## <a name="syntax"></a>语法

```C
void __debugbreak();
```

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`__debugbreak`|x86、x64、ARM、ARM64|\<intrin.h>|

## <a name="remarks"></a>备注

`__debugbreak`编译器内部函数（类似于 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak)）是导致断点的可移植 Win32 方法。

> [!NOTE]
> 使用 **/clr**进行编译时，包含`__debugbreak`的函数将编译为 MSIL。 `asm int 3` 可将函数编译为本机函数。 有关详细信息，请参阅[__asm](../assembler/inline/asm.md)。

例如:

```C
main() {
   __debugbreak();
}
```

类似于：

```C
main() {
   __asm {
      int 3
   }
}
```

在 x86 计算机上。

在 ARM64 上， `__debugbreak`将内部函数编译到指令`brk #0xF000`中。

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[关键字](../cpp/keywords-cpp.md)
