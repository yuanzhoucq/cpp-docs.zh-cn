---
title: "/H（限制外部名称长度） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/h"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/H 编译器选项 [C++]"
  - "外部名称"
  - "H 编译器选项 [C++]"
  - "-H 编译器选项 [C++]"
  - "公共名称长度"
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /H（限制外部名称长度）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

限制外部名称的长度。  
  
## 语法  
  
```  
/Hnumber  
```  
  
## Arguments  
 `number`  
 指定程序中允许的外部名称的最大长度。  
  
## 备注  
 默认情况下，外部（公共）名称的长度为 2,047 个字符。  对于 C 和 C\+\+ 程序的确如此。  使用 **\/H** 只能减少标识符的最大允许长度，而不能增加其长度。  **\/H** 和 `number` 之间的空格为可选。  
  
 如果程序包含长于 `number` 的外部名称，则忽略多余字符。  如果编译程序时没有用 **\/H** 且某个标识符包含的字符多于 2,047 个，则编译器将生成 [错误 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)。  
  
 长度限制包括任何编译器创建的前导下划线 \(\_\) 或“at”符 \(@\)。  这些字符是标识符的一部分并占用有效位置。  
  
-   编译器将前导下划线 \(\_\) 添加到由 `__cdecl`（默认）和 `__stdcall` 调用约定修饰的名称，将前导“at”符 \(@\) 添加到由 `__fastcall` 调用约定修饰的名称。  
  
-   编译器将参数大小信息追加到由 `__fastcall` 和 `__stdcall` 调用约定修饰的名称，将类型信息添加到 C\+\+ 名称。  
  
 您可能会发现 **\/H** 非常有用：  
  
-   当创建混合语言或可移植程序时。  
  
-   当使用限制外部标识符长度的工具时。  
  
-   当希望限制在调试版本中符号使用的空间量时。  
  
 下面的示例演示如果过度限制标识符长度，则使用 **\/H** 将能如何实际引入错误：  
  
```  
// compiler_option_H.cpp  
// compile with: /H5  
// processor: x86  
// LNK2005 expected  
void func1(void);  
void func2(void);  
  
int main() { func1(); }  
  
void func1(void) {}  
void func2(void) {}  
```  
  
 使用 **\/H** 选项时还必须小心谨慎，因为存在预定义编译器标识符。  如果最大标识符长度太小，则将无法解析某些预定义标识符以及某些库函数调用。  例如，如果使用 `printf` 函数并在编译时指定 **\/H5** 选项，则将创建 **\_prin** 符号以便引用 `printf`，而在库中将找不到此符号。  
  
 **\/H** 的使用与 [\/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md) 不兼容。  
  
 不推荐使用 **\/H**；最大长度限制已经增加，不再需要 **\/H**。有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)