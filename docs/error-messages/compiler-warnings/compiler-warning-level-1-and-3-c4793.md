---
title: 编译器警告（等级 1 和等级 3）C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: de6f514d8e3ad8e7715c9cd13a695e3398fffc8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164802"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>编译器警告（等级 1 和等级 3）C4793

> "*function*"：函数编译为本机代码： "*reason*"

## <a name="remarks"></a>备注

即使指定了[/clr](../../build/reference/clr-common-language-runtime-compilation.md)编译器选项，编译器也无法将*函数*编译为托管代码。 相反，编译器会发出警告 C4793 和解释性的延续消息，然后将*函数*编译为本机代码。 继续消息包含说明为什么无法将*函数*编译为 `MSIL`的*原因*文本。

指定 **/clr： pure**编译器选项时，这是1级警告。  **/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

下表列出了所有可能的延续消息。

|原因消息|备注|
|--------------------|-------------|
|托管代码中不支持对齐数据类型|CLR 必须能够根据需要分配数据，如果数据与[__m128](../../cpp/m128.md)或[align](../../cpp/align-cpp.md)等声明对齐，则这可能是不可能的。|
|托管代码中不支持使用 "__ImageBase" 的函数|`__ImageBase` 是一种特殊的链接器符号，通常仅由低级别本机代码用来加载 DLL。|
|"/clr" 编译器选项不支持 varargs|本机函数无法调用具有[变量参数列表](../../cpp/functions-with-variable-argument-lists-cpp.md)（varargs）的托管函数，因为函数具有不同的堆栈布局要求。 但是，如果指定 **/clr： pure**编译器选项，则支持变量参数列表，因为该程序集只能包含托管函数。 有关详细信息，请参阅[纯代码和可C++验证代码（/cli）](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。|
|64位 CLR 不支持用 __ptr32 修饰符声明的数据|指针的大小必须与当前平台上的本机指针的大小相同。 有关详细信息，请参阅[__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md)。|
|32位 CLR 不支持用 __ptr64 修饰符声明的数据|指针的大小必须与当前平台上的本机指针的大小相同。 有关详细信息，请参阅[__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md)。|
|托管代码中不支持一个或多个内部函数|发出消息时，内部函数的名称不可用。 但是，导致此消息的内部函数通常表示低级计算机指令。|
|托管代码中不支持内联本机程序集（"__asm"）|[内联程序集代码](../../assembler/inline/asm.md)可以包含无法管理的任意本机代码。|
|非 __clrcall 虚函数 thunk 必须编译为本机|非[__clrcall](../../cpp/clrcall.md)虚函数 thunk 必须使用非托管地址。|
|使用 "_setjmp" 的函数必须编译为本机函数|CLR 必须能够控制程序执行。 但是，通过保存和还原低级信息（如寄存器和执行状态）， [setjmp](../../cpp/using-setjmp-longjmp.md)函数会绕过常规程序执行。|

## <a name="example"></a>示例

下面的示例生成 C4793。

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

下面的示例生成 C4793。

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```
