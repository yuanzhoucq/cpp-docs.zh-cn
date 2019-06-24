---
title: __debugbreak
ms.date: 11/04/2016
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: 97932dfe0e187a13b72ae5fe70d761224721c3ff
ms.sourcegitcommit: 1acb6755e11379026a96f63facac4d33f4dc47ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2019
ms.locfileid: "67314260"
---
# <a name="debugbreak"></a>__debugbreak

**Microsoft 专用**

将在代码中引起断点，并在其中提示用户运行调试程序。

## <a name="syntax"></a>语法

```
void __debugbreak();
```

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`__debugbreak`|x86、 x64、 ARM，ARM64|\<intrin.h>|

## <a name="remarks"></a>备注

`__debugbreak`编译器内部函数，类似于[DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx)，是会导致断点的可移植 Win32 方式。

> [!NOTE]
>  使用编译时 **/clr**，一个函数，其中包含`__debugbreak`将编译为 MSIL。 `asm int 3` 可将函数编译为本机函数。 有关详细信息，请参阅[__asm](../assembler/inline/asm.md)。

例如：

```
main() {
   __debugbreak();
}
```

类似于：

```
main() {
   __asm {
      int 3
   }
}
```

在 x86 计算机上。

ARM64 上,`__debugbreak`内部函数编译为指令`brk #0xF000`。

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)
