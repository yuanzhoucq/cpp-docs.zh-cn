---
title: "/D（预处理器定义） | Microsoft Docs"
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
  - "VC.Project.VCNMakeTool.PreprocessorDefinitions"
  - "VC.Project.VCCLCompilerTool.PreprocessorDefinitions"
  - "/d"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/D 编译器选项 [C++]"
  - "常量, 定义"
  - "D 编译器选项 [C++]"
  - "-D 编译器选项 [C++]"
  - "宏, 编译"
  - "预处理器定义符号"
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /D（预处理器定义）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义源文件的预处理符号。  
  
## 语法  
  
```  
/Dname[= | # [{string | number}] ]  
```  
  
## 备注  
 可以将此符号与 `#if` 或 `#ifdef` 一起使用，以便有条件地编译源代码。  在代码中重新定义或通过 `#undef` 指令在代码中取消定义符号前，符号定义保持有效。  
  
 **\/D** 与源代码文件开头的 `#define` 指令具有相同的效果，只不过 **\/D** 会去除命令行上的引号，而 `#define` 会保留它们。  
  
 默认情况下，与符号关联的值为 1。  例如，**\/D**`name` 等效于 **\/D**`name`**\=1**。  在本文末尾的示例中，显示 **TEST** 的定义以输出 `1`。  
  
 使用 **\/D**`name`**\=** 进行编译将导致符号没有关联值。  尽管该符号仍可用于有条件地编译代码，但它不会计算出任何结果。  在本示例中，如果使用 **\/DTEST\=** 进行编译，则会发生错误。  此行为类似于带或不带值使用 `#define`。  
  
 此命令在 TEST.c 中定义符号 DEBUG：  
  
 **CL \/DDEBUG  TEST.C**  
  
 此命令移除 TEST.c 中关键字 `__far` 的所有匹配项：  
  
 **CL \/D\_\_far\=  TEST.C**  
  
 不能将 **CL** 环境变量设置为包含等号的字符串。  若要将 **\/D** 与 **CL** 环境变量一起使用，则必须指定数字符号而非等号：  
  
```  
SET CL=/DTEST#0  
```  
  
 在命令提示符处定义预处理符号时，应同时考虑编译器分析规则和 shell 分析规则。  例如，若要在程序中定义百分号预处理符号 \(%\)，请在命令提示符处指定两个百分号字符 \(%%\)：如果只指定一个，则会发出分析错误。  
  
```  
CL /DTEST=%% TEST.C  
```  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在左窗格中，依次选择**“配置属性”**、**“C\/C\+\+”**和**“预处理器”**。  
  
3.  在右窗格中的**“预处理器定义”**属性的右列中，打开下拉菜单并选择**“编辑”**。  
  
4.  在**“预处理器定义”**对话框中，添加（每行一个）、修改、或删除一个或多个定义。  选择**“确定”**以保存更改。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>。  
  
## 示例  
  
```  
// cpp_D_compiler_option.cpp  
// compile with: /DTEST  
#include <stdio.h>  
  
int main( )  
{  
    #ifdef TEST  
        printf_s("TEST defined %d\n", TEST);  
    #else  
        printf_s("TEST not defined\n");  
    #endif  
}  
```  
  
  **TEST defined 1**   
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [\/U、\/u（未定义符号）](../../build/reference/u-u-undefine-symbols.md)   
 [\#undef 指令](../../preprocessor/hash-undef-directive-c-cpp.md)   
 [\#define 指令](../../preprocessor/hash-define-directive-c-cpp.md)