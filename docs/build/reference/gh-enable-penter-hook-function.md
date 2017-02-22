---
title: "/Gh（启用 _penter 挂钩函数） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_penter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gh 编译器选项 [C++]"
  - "_penter 函数"
  - "Gh 编译器选项 [C++]"
  - "-Gh 编译器选项 [C++]"
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /Gh（启用 _penter 挂钩函数）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导致在每个方法或函数的开头调用 `_penter` 函数。  
  
## 语法  
  
```  
/Gh  
```  
  
## 备注  
 `_penter` 函数不是任何库的组成部分，由您负责提供 `_penter` 的定义。  
  
 除非打算显式调用 `_penter`，否则不需要提供原型。  该函数必须看起来似乎具有下列原型，并且必须在进入时推送所有寄存器的内容，在退出时弹出未更改的内容：  
  
```  
void __declspec(naked) _cdecl _penter( void );  
```  
  
 此声明不适用于 64 位项目。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 示例  
 当用 **\/Gh** 编译时，以下代码显示如何两次调用 `_penter`；一次是在进入函数 `main` 时，一次是在进入函数 `x` 时。  
  
```  
// Gh_compiler_option.cpp  
// compile with: /Gh  
// processor: x86  
#include <stdio.h>  
void x() {}  
  
int main() {  
   x();  
}  
  
extern "C" void __declspec(naked) _cdecl _penter( void ) {  
   _asm {  
      push eax  
      push ebx  
      push ecx  
      push edx  
      push ebp  
      push edi  
      push esi  
    }  
  
   printf_s("\nIn a function!");  
  
   _asm {  
      pop esi  
      pop edi  
      pop ebp  
      pop edx  
      pop ecx  
      pop ebx  
      pop eax  
      ret  
    }  
}  
```  
  
  **在函数中！**  
**在函数中！**   
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)