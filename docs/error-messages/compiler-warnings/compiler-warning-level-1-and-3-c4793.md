---
title: "编译器警告（等级 1 和等级 3）C4793 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4793"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4793"
  - "C6630"
  - "C6631"
  - "C6634"
  - "C6635"
  - "C6636"
  - "C6637"
  - "C6638"
  - "C6639"
  - "C6640"
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1 和等级 3）C4793
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数编译为本机代码: “reason”  
  
 即便已指定 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译器选项，编译器也无法将*function*编译为托管代码。  相反，编译器将发出警告 C4793 和说明性的连续消息，然后将*function*编译为本机代码。  连续消息包含*reason* 文本，解释为何不能将*function*编译为 `MSIL`  
  
 当指定 `/clr:pure` 编译器选项时，这是 1 级警告。  
  
 下表列出了所有可能的连续消息。  
  
|原因消息|备注|  
|----------|--------|  
|托管代码中不支持对齐数据类型|CLR 必须能够根据需要分配数据，如果数据与 [\_\_m128](../../cpp/m128.md) 或 [align](../../cpp/align-cpp.md) 等声明对齐，则 CLR 可能无法分配数据。|  
|托管代码中不支持使用“\_\_ImageBase”的函数|`__ImageBase` 是特殊的链接器符号，通常仅由低级别的本机代码用以加载 DLL。|  
|“\/clr”编译器选项不支持 varargs|本机函数不能调用具有[变量参数列表](../../misc/variable-argument-lists.md) \(varargs\) 的托管函数，因为这些函数有不同的堆栈布局要求。  但是，如果指定 `/clr:pure` 编译器选项，则将支持变量参数列表，因为程序集仅包含托管函数。  有关详细信息，请参阅[纯代码和可验证代码](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。|  
|64 位 CLR 不支持用 \_\_ptr32 修饰符声明的数据|指针的大小必须与当前平台上的本机指针的大小相同。  有关详细信息，请参阅[\_\_ptr32、\_\_ptr64](../../cpp/ptr32-ptr64.md)。|  
|32 位 CLR 不支持用 \_\_ptr64 修饰符声明的数据|指针的大小必须与当前平台上的本机指针的大小相同。  有关详细信息，请参阅[\_\_ptr32、\_\_ptr64](../../cpp/ptr32-ptr64.md)。|  
|托管代码中不支持一个或多个内部函数|内部函数的名称在消息发出时不可用。  但是，导致此消息的内部函数通常表示低级别的机器指令。|  
|托管代码中不支持内联本机程序集\(“\_\_asm”\)|[内联程序集代码](../../assembler/inline/asm.md)可以包含无法托管的任意本机代码。|  
|非 \_\_clrcall 虚函数形式转换\(thunk\)必须编译为本机|非 [\_\_clrcall](../../cpp/clrcall.md) 虚函数形式转换 \(thunk\) 必须使用非托管地址。|  
|使用“\_setjmp”的函数必须编译为本机|CLR 必须能够控制程序执行。  但是，[setjmp](../../cpp/using-setjmp-longjmp.md) 函数通过保存和还原低级别信息（如注册和执行状态）可忽略常规程序执行。|  
  
## 示例  
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
  
  **警告 C4793:“asmfunc”: 函数编译为本机代码:**  
 **托管代码中不支持内联本机程序集\(“\_\_asm”\)**   
## 示例  
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
  
  **警告 C4793:“f”: 函数编译为本机代码:**  
 **使用“\_setjmp”的函数必须编译为本机**