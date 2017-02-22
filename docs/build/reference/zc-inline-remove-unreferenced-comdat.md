---
title: "/Zc:inline（移除未引用的 COMDAT） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:inline"
  - "VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 编译器选项 (C++)"
  - "/Zc:inline"
  - "Zc 编译器选项 (C++)"
  - "-Zc 编译器选项 (C++)"
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /Zc:inline（移除未引用的 COMDAT）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移除为 COMDAT 或只具有内部链接的未引用函数或数据。  指定 **\/Zc:inline** 时，编译器要求使用内联数据或内联函数的翻译单元还必须包括数据或函数的定义。  
  
## 语法  
  
```  
/Zc:inline[-]  
```  
  
## 备注  
 指定 **\/Zc:inline** 时，编译器不会发出未引用的 COMDAT 函数或数据或者只具有内部链接的函数或数据的符号信息。  默认情况下，此选项 \(**\/Zc:inline\-**\) 处于关闭状态。  此优化将简化在发布生成中或在指定链接器选项 [\/OPT:REF](../../build/reference/opt-optimizations.md) 时链接器所执行的一些工作。  编译器执行此优化后，可显著减小 .obj 文件大小并提高链接器速度。  当禁用优化 \([\/Od](../../build/reference/od-disable-debug.md)\) 或指定 [\/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md) 时，不会启用此编译器选项。  
  
 如果指定 **\/Zc:inline**，则编译器强制执行 C\+\+11 要求，所有声明为 `inline` 的函数都必须具有在同一转换单元中（如果使用了这些函数）可用的定义。  未指定该选项时，即使没有可见定义，[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 仍允许调用声明为 `inline` 的函数的不一致代码。  有关详细信息，请参阅 3.2 节和 7.1.2 节中的 C\+\+11 标准。  Visual Studio 2013 Update 2 中引入了此编译器选项。  
  
 若要使用 **\/Zc:inline** 选项，请更新不兼容的代码。  此示例显示在使用默认 **\/Zc:inline\-** 选项时，在不符合规定地使用没有定义的内联函数声明的情况下，仍然能够进行编译和链接的方式：  
  
```cpp  
// example.h  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#pragma once  
  
class Example {  
public:  
   inline void inline_call(); // declared but not defined inline  
   void normal_call();  
   Example() {};  
};  
```  
  
```cpp  
// example.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#include <stdio.h>  
#include "example.h"  
  
void Example::inline_call() {  
   printf("inline_call was called.\n");   
}  
  
void Example::normal_call() {  
   printf("normal_call was called.\n");   
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file  
}  
```  
  
```cpp  
// zcinline.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#include "example.h"  
  
void main() {  
   Example example;  
   example.inline_call(); // normal call when definition unavailable  
}  
```  
  
 启用 **\/Zc:inline** 时，相同的代码会导致 [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) 错误，因为编译器未在 example.obj 中发出 `Example::inline_call` 的非内联代码体。  这会导致 `main` 中的非内联调用以引用未定义的外部符号。  
  
 若要解决此错误，可从 `Example::inline_call` 的声明中移除 `inline` 关键字、将 `Example::inline_call` 的定义移到头文件中，或将 `Example` 的实现移到 main.cpp 中。  下一个示例将定义移到头文件中，其中该定义对包含该头文件的所有调用方都可见。  
  
```cpp  
// example2.h  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#pragma once  
#include <stdio.h>  
  
class Example2 {  
public:  
   inline void inline_call() {  
      printf("inline_call was called.\n");   
   }  
   void normal_call();  
   Example2() {};  
};  
```  
  
```cpp  
// example2.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#include "example2.h"  
  
void Example2::normal_call() {  
   printf("normal_call was called.\n");   
   inline_call();   
}  
```  
  
```cpp  
// zcinline2.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#include "example2.h"  
  
void main() {  
   Example2 example2;  
   example2.inline_call(); // normal call when definition unavailable  
}  
```  
  
 有关 Visual C\+\+ 中的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  修改**“附加选项”**属性以包含 `/Zc:inline`，然后选择**“确定”**。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)