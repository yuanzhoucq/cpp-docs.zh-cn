---
title: "/Os、/Ot（代码大小优先、代码速度优先） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed"
  - "/os"
  - "VC.Project.VCCLCompilerTool.FavorSizeOrSpeed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Os 编译器选项 [C++]"
  - "/Ot 编译器选项 [C++]"
  - "快速代码"
  - "代码速度优先编译器选项 [C++]"
  - "代码大小优先编译器选项 [C++]"
  - "Os 编译器选项 [C++]"
  - "-Os 编译器选项 [C++]"
  - "Ot 编译器选项 [C++]"
  - "-Ot 编译器选项 [C++]"
  - "小型机器代码"
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Os、/Ot（代码大小优先、代码速度优先）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

最小化或最大化 EXE 和 DLL 的大小。  
  
## 语法  
  
```  
/Os  
/Ot  
```  
  
## 备注  
 **\/Os**（代码大小优先）通过指示编译器优选大小而非速度来最小化 EXE 和 DLL 的大小。  编译器可以将许多 C 和 C\+\+ 构造缩小为功能类似的机器码序列。  这些差异有时在大小和速度之间提供了折中。  **\/Os** 和 **\/Ot** 选项允许在二者之间指定一个首选项：  
  
 **\/Ot**（代码速度优先）通过指示编译器优选速度而非大小来最大化 EXE 和 DLL 的速度。（这是默认设置。）编译器可以将许多 C 和 C\+\+ 构造缩小为功能类似的机器码序列。  这些差异有时在大小和速度之间提供了折衷。  “最大化速度”\([\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)\) 选项隐含 \/Ot 选项。  **\/O2** 选项组合若干个选项以产生速度非常快的代码。  
  
 如果使用 **\/Os** 或 **\/Ot**，还必须指定 [\/Og](../../build/reference/og-global-optimizations.md) 以优化代码。  
  
> [!NOTE]
>  如果您指定 **\/Ob**、**\/Os** 或 **\/Ot**，则从分析测试运行收集的信息会重写本可以生效的优化。  有关更多信息，请参见[按配置文件优化](../../build/reference/profile-guided-optimizations.md)。  
  
 **x86 专用**  
  
 下面的代码示例说明“代码大小优先”\(**\/Os**\) 选项和“代码速度优先”\(**\/Ot**\) 选项之间的差异：  
  
> [!NOTE]
>  下面的内容描述使用 **\/Os** 或 **\/Ot** 时的预期行为。  但是，由于在各版本的编译器行为不相同，因此可能导致对以下代码进行不同的优化。  
  
```  
/* differ.c  
  This program implements a multiplication operator  
  Compile with /Os to implement multiply explicitly as multiply.  
  Compile with /Ot to implement as a series of shift and LEA instructions.  
*/  
int differ(int x)  
{  
    return x * 71;  
}  
```  
  
 如下面的机器码片段所示，当出于大小考虑 \(**\/Os**\) 编译 DIFFER.c 时，编译器将返回语句中的乘法表达式显式实现为乘法，以产生短小但较慢的代码序列：  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
imul   eax, 71                  ; 00000047H  
```  
  
 或者，当出于速度考虑 \(**\/Ot**\) 编译 DIFFER.c 时，编译器将返回语句中的乘法表达式实现为一系列移位指令和 `LEA` 指令，以产生执行速度快但较长的代码序列：  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
mov    ecx, eax  
shl    eax, 3  
lea    eax, DWORD PTR [eax+eax*8]  
sub    eax, ecx  
```  
  
 **END x86 Specific**  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“优化”**属性页。  
  
4.  修改**“优选大小或速度”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)