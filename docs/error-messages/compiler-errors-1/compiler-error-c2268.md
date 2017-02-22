---
title: "编译器错误 C2268 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2268"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2268"
ms.assetid: 0ed055c9-3c6f-4df2-a5b6-85cf0e01a249
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2268
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”是编译器预定义的库帮助器。 系统不支持使用 \/GL 的库帮助器，编译对象文件“file”时不要使用 \/GL。  
  
 源代码中定义的函数与内部编译器函数具有相同的名称。 编译包含函数的模块时不要使用 [\/GL](../../build/reference/gl-whole-program-optimization.md)。  
  
 下面的示例生成 C2268：  
  
```  
// C2268.c // compile with: /c // processor: x86 extern int SHFusionLoadLibrary(int lpLibFileName); int __cdecl _except_handler3(void) { return SHFusionLoadLibrary(0); } extern int main(void); void* mainCRTStartup(void* p) { p = main; return p; }  
```  
  
 然后：  
  
```  
// C2268b.c // compile with: C2268.c /EHsc /GL /Ob0 /O2 /Fa /GS- /link /nodefaultlib // processor: x86 extern int SHFusionLoadLibrary(int lpLibFileName); extern int __cdecl _except_handler3(void); extern void mainCRTStartup(void*); int g = 2; #define ENTERCONTEXT(fail) \ int ulCookie = 0;\ if (!SHActivateContext(&ulCookie)) \ return fail;\ __try { #define LEAVECONTEXT \ } __finally {SHDeactivateContext(ulCookie);} int SHActivateContext(int* a) { return *a == g || !*a ||_except_handler3(); } void SHDeactivateContext(int a) { g = a; } int SHFusionLoadLibrary(int lpLibFileName) {   // C2268 ENTERCONTEXT(0) g = lpLibFileName; LEAVECONTEXT return lpLibFileName; } int main(void) { g = SHFusionLoadLibrary(10); return 0; }  
```