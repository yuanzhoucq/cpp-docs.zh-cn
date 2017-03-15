---
title: "/RTC（运行时错误检查） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rtc"
  - "VC.Project.VCCLCompilerTool.SmallerTypeCheck"
  - "VC.Project.VCCLCompilerTool.UninitializedVariableCheck"
  - "VC.Project.VCCLCompilerTool.StackFrameCheck"
  - "VC.Project.VCCLCompilerTool.BasicRuntimeChecks"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RTC1 编译器选项 [C++]"
  - "/RTCc 编译器选项 [C++]"
  - "/RTCs 编译器选项 [C++]"
  - "/RTCu 编译器选项 [C++]"
  - "__MSVC_RUNTIME_CHECKS 宏"
  - "RTC1 编译器选项"
  - "-RTC1 编译器选项 [C++]"
  - "RTCc 编译器选项"
  - "-RTCc 编译器选项 [C++]"
  - "RTCs 编译器选项"
  - "-RTCs 编译器选项 [C++]"
  - "RTCu 编译器选项"
  - "-RTCu 编译器选项 [C++]"
  - "运行时检查, /RTC 选项"
  - "运行时错误, 错误检查"
  - "运行时错误, 运行时检查"
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /RTC（运行时错误检查）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于启用和禁用运行时错误检查功能，与 [runtime\_checks](../../preprocessor/runtime-checks.md) 杂注一起使用。  
  
## 语法  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## Arguments  
 `1`  
 **\/RTC** `su` 的等效项。  
  
 `c`  
 当向较小的数据类型赋值从而导致数据丢失时报告。  例如，当将类型 `short 0x101` 的值赋给类型 `char` 的变量时。  
  
 此选项报告您打算截断的情况，例如，您希望将 `int` 的前八位作为 `char` 返回的情况。  因为 **\/RTC**`c` 在由于赋值而丢失任何信息时将导致运行时错误，您可以屏蔽所需的信息以避免由于 **\/RTC**`c` 而产生的运行时错误。  例如：  
  
```  
#include <crtdbg.h>  
  
char get8bits(int value, int position) {  
   _ASSERT(position < 32);  
   return (char)(value >> position);  
   // Try the following line instead:  
   // return (char)((value >> position) & 0xff);  
}  
  
int main() {  
   get8bits(12341235,3);  
}  
```  
  
 `s`  
 启用堆栈帧运行时错误检查，如下所示：  
  
-   将局部变量初始化为非零值。  这有助于识别在调试模式下运行时不出现的 bug。  因为在发布版本中编译器对堆栈变量进行优化，所以与发布版本相比，堆栈变量在调试版本中仍然为零的可能性更大。  一旦程序使用其堆栈区域后，它就永远不会由编译器重置为 0。  因此，恰好在随后使用相同堆栈区域的未初始化堆栈变量就可能返回上次使用该堆栈内存时留下的值。  
  
-   检测局部变量（如数组）的溢出和不足。  **\/RTC**`s` 将不检测当访问内存时由结构内的编译器填充导致的溢出。  当使用 [align](../../cpp/align-cpp.md)、[\/Zp（结构成员对齐）](../../build/reference/zp-struct-member-alignment.md) 或 [pack](../../preprocessor/pack.md) 时，或者以某种方式对结构元素进行排序以致要求编译器添加填充时，可能发生填充。  
  
-   堆栈指针验证，该操作检测堆栈指针损坏。  调用约定不匹配可能导致堆栈指针损坏。  例如，使用函数指针调用 DLL 中作为 [\_\_stdcall](../../cpp/stdcall.md) 导出的函数，但将指向该函数的指针声明为 [\_\_cdecl](../../cpp/cdecl.md)。  
  
 `u`  
 当使用的变量尚未初始化时进行报告。  例如，生成 `C4701` 的指令也可能在 **\/RTC**`u` 下生成运行时错误。  生成 [编译器警告（等级 1 和等级 4）C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) 的任何指令将在 **\/RTC**`u` 下生成运行时错误。  
  
 然而，请考虑下列代码片段：  
  
```  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 如果变量可能已经初始化，则 **\/RTC**`u` 在运行时将不报告。  例如，在通过指针为变量起别名以后，编译器将不再跟踪此变量并报告未初始化使用。  实际上，可以通过获取其地址来初始化变量。  在这种情况下， &运算符的作用类似于赋值运算符。  
  
## 备注  
 运行时错误检查是发现运行的代码中的问题的一种途径；有关更多信息，请参见 [如何：使用本机运行时检查](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md)。  
  
 如果在命令行上使用任一 **\/RTC** 编译器选项编译程序，代码中的任何杂注 [optimize](../../preprocessor/optimize.md) 指令将失败而不给出任何提示。  这是因为运行时错误检查在发布（优化）版本中无效。  
  
 对于开发版本，应该使用 **\/RTC**；对于零售版本，不应使用 **\/RTC**。  **\/RTC** 不能与编译器优化 \([\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)\) 一起使用。  与用 **\/Od** 生成的映像相比，用 **\/RTC** 生成的程序映像稍大一些，速度也稍慢一些（最多比 **\/Od** 版本慢 5%）。  
  
 当使用任何 **\/RTC** 选项或 [\/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) 时，将定义 \_\_MSVC\_RUNTIME\_CHECKS 预处理器指令。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“代码生成”**属性页。  
  
4.  修改下列属性之一或两者都修改：**“基本运行时检查”**或**“较小类型检查”**。  
  
### 以编程方式设置此编译器选项  
  
-   请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 属性。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [RTC sample](http://msdn.microsoft.com/zh-cn/b3415b09-f6fd-43dc-8c02-9a910bc2574e)