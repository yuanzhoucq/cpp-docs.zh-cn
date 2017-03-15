---
title: "链接器工具警告 LNK4049 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4049"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4049"
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# 链接器工具警告 LNK4049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已导入本地定义的符号“symbol”  
  
 该符号被同时从程序导出和导入到程序中。  
  
 当使用一个对象文件中的 `__declspec(dllexport)` 存储类特性声明符号，但使用另一对象文件中的 `__declspec(dllimport)` 特性引用该符号时，链接器将生成此警告。  
  
 警告 LNK4049 是[链接器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md) 的更为常见的形式。  当链接器无法确定从哪个函数引用的导入符号时便会生成警告 LNK4049。  
  
 下面是生成 LNK4049 而不是 LNK4217 的常见情况：  
  
-   使用 [\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) 选项执行增量链接。  
  
-   使用 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 选项执行全程序优化。  
  
 若要解决 LNK4049 问题，请执行以下操作之一：  
  
-   从触发 LNK4049 的符号的前向声明中移除 `__declspec(dllimport)` 名称声明。  您可以使用 **DUMPBIN** 实用工具在二进制图像中搜索符号。  **DUMPBIN \/SYMBOLS** 开关可显示该图像的 COFF 符号表。  有关 **DUMPBIN** 实用工具的更多信息，请参见 [DUMPBIN 参考](../../build/reference/dumpbin-reference.md)。  
  
-   暂时禁用增量链接和全程序优化。  重新编译该应用程序将生成警告 LNK4217，警告中将包含从中引用所导入符号的函数的名称。  请从导入的符号中移除 `__declspec(dllimport)` 声明，然后根据需要启用增量链接或全程序优化。  
  
 尽管最终生成的代码可以正常运行，不过，生成代码来调用导入的函数比直接调用该函数效率低。  使用选项 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 进行编译时不会出现此警告。  
  
 有关导入和导出数据声明的更多信息，请参见 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)。  
  
## 示例  
 链接以下两个模块将生成 LNK4049。  第一个模块生成一个对象文件，其中包含单个导出函数。  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## 示例  
 第二个模块生成一个对象文件，其中包含对第一个模块中导出的函数的前向声明以及在 `main` 函数中对此函数的调用。  将此模块与第一个模块相链接将生成 LNK4049。  移除 `__declspec(dllimport)` 声明将消除该警告。  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## 请参阅  
 [链接器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)