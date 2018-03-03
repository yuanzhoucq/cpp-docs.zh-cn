---
title: "-Zc： 内联 （移除未引用的 COMDAT） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c8d14f6055c96f5c9feed16d2ad0b996f0d0b94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline（移除未引用的 COMDAT）
移除为 COMDAT 或只具有内部链接的未引用函数或数据。 当**/zc: inline**指定，编译器要求使用内联数据或内联函数的翻译单元还必须包括数据或函数的定义。  
  
## <a name="syntax"></a>语法  
  
```  
/Zc:inline[-]  
```  
  
## <a name="remarks"></a>备注  
 当**/zc: inline**指定，编译器不发出符号信息未引用的 COMDAT 函数或数据，或只具有内部链接的函数或数据。 默认情况下，此选项处于关闭状态 (**/Zc:inline-**)。 此优化将简化某些发布版本的链接器所执行的工作时，或者当链接器选项[/opt: ref](../../build/reference/opt-optimizations.md)指定。 编译器执行此优化后，可显著减小 .obj 文件大小并提高链接器速度。 禁用优化后未启用此编译器选项 ([/Od](../../build/reference/od-disable-debug.md)) 时，或者当[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)指定。  
  
 如果**/zc: inline**指定，则编译器强制执行的 C + + 11 要求所有函数都声明`inline`必须具有可用在同一个翻译单元中的定义，如果使用了它们。 未指定该选项时，即使没有可见定义，[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 仍允许调用声明为 `inline` 的函数的不一致代码。 有关详细信息，请参阅 3.2 节和 7.1.2 节中的 C++11 标准。 Visual Studio 2013 Update 2 中引入了此编译器选项。  
  
 若要使用**/zc: inline**选项，请更新不符合标准代码。 此示例演示如何没有定义的内联函数声明不符合使用仍将编译并链接时默认**/Zc:inline-**使用选项：  
  
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
  
 当**/zc: inline**启用时，相同的代码会导致[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)错误，因为编译器不发出的非内联代码体`Example::inline_call`在 example.obj 中发出。这会导致 `main` 中的非内联调用以引用未定义的外部符号。  
  
 若要解决此错误，可从 `inline` 的声明中移除 `Example::inline_call` 关键字、将 `Example::inline_call` 的定义移到头文件中，或将 `Example` 的实现移到 main.cpp 中。 下一个示例将定义移到头文件中，其中该定义对包含该头文件的所有调用方都可见。  
  
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
  
 有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  修改**其他选项**属性以包含`/Zc:inline`，然后选择**确定**。  
  
## <a name="see-also"></a>请参阅  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)