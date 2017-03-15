---
title: "编译器警告 （等级 1 和 3） C4793 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4793
dev_langs:
- C++
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
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: a217d2074affa1598aef93882fb299c6fcdef5a6
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-and-3-c4793"></a>编译器警告（等级 1 和等级 3）C4793
function︰ 函数编译为本机代码: reason  
  
 编译器将无法编译*函数*入托管代码，即使[/clr](../../build/reference/clr-common-language-runtime-compilation.md)指定编译器选项。 相反，编译器发出警告 C4793 和说明性的连续消息，并进行编译*函数*到本机代码。 连续消息包含*原因*文本，解释为什么*函数*不能编译为`MSIL`。  
  
 这是一个 1 级警告，当您指定`/clr:pure`编译器选项。  **/Clr: pure**编译器选项已弃用 Visual Studio 2015 中。  
  
 下表列出所有可能的连续消息。  
  
|原因消息|备注|  
|--------------------|-------------|  
|在托管代码中不支持对齐的数据类型|CLR 必须能够分配数据，根据需要这可能不可行的如果数据对齐与声明如[__m128](../../cpp/m128.md)或[对齐](../../cpp/align-cpp.md)。|  
|在托管代码中不支持使用 '__ImageBase' 的函数|`__ImageBase`是一个特殊的链接器符号，通常用于仅由低级别的本机代码加载 DLL。|  
|不支持 varargs ' / clr 编译器选项|本机函数不能调用具有托管的函数，[变量参数列表](../../cpp/functions-with-variable-argument-lists-cpp.md)(varargs) 因为这些函数有不同的堆栈布局要求。 但是，如果您指定`/clr:pure`编译器选项时，支持变量参数列表是因为该程序集可以仅包含托管函数。 有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。|  
|64 位 CLR 不支持用 __ptr32 修饰符声明的数据|一个指针，必须是与当前平台的本机指针的大小相同。 有关详细信息，请参阅[__ptr32、 \__ptr64](../../cpp/ptr32-ptr64.md)。|  
|32 位 CLR 不支持用 __ptr64 修饰符声明的数据|一个指针，必须是与当前平台的本机指针的大小相同。 有关详细信息，请参阅[__ptr32、 \__ptr64](../../cpp/ptr32-ptr64.md)。|  
|托管代码中不支持一个或多个内部函数|在发出消息的时间内部函数的名称不可用。 但是，内部函数，通常会导致该消息表示低级别的机器指令。|  
|托管代码中不支持内联本机程序集 (__asm)|[内联程序集代码](../../assembler/inline/asm.md)可以包含任意无法管理的本机代码。|  
|非 __clrcall 虚函数转换 （thunk） 必须编译为本机|非[__clrcall](../../cpp/clrcall.md)虚函数转换 （thunk） 必须使用非托管的地址。|  
|使用 _setjmp' 的函数必须编译为本机|CLR 必须能够控制程序执行。 但是， [setjmp](../../cpp/using-setjmp-longjmp.md)函数忽略通过保存和还原低级别的信息，如注册和执行状态的常规程序执行。|  
  
## <a name="example"></a>示例  
 下面的示例生成 C4793。  
  
```  
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
  
## <a name="example"></a>示例  
 下面的示例生成 C4793。  
  
```  
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
