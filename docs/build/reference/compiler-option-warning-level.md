---
title: "/w、/Wn、/WX、/Wall、/wln、/wdn、/wen、/won（警告等级） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.DisableSpecificWarnings"
  - "VC.Project.VCCLCompilerTool.WarningLevel"
  - "VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings"
  - "VC.Project.VCCLCompilerTool.WarnAsError"
  - "VC.Project.VCCLWCECompilerTool.WarnAsError"
  - "/wx"
  - "VC.Project.VCCLWCECompilerTool.WarningLevel"
  - "/wall"
  - "VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors"
  - "/Wv"
  - "/w0"
  - "/w1"
  - "/w2"
  - "/w3"
  - "/w4"
  - "/wd"
  - "/we"
  - "/wo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/w 编译器选项"
  - "/W0 编译器选项 [C++]"
  - "/W1 编译器选项 [C++]"
  - "/W2 编译器选项 [C++]"
  - "/W3 编译器选项 [C++]"
  - "/W4 编译器选项 [C++]"
  - "/Wall 编译器选项 [C++]"
  - "/wd 编译器选项 [C++]"
  - "/we 编译器选项 [C++]"
  - "/wo 编译器选项 [C++]"
  - "/WX 编译器选项 [C++]"
  - "w 编译器选项 [C++]"
  - "-w 编译器选项 [C++]"
  - "W0 编译器选项 [C++]"
  - "-W0 编译器选项 [C++]"
  - "W1 编译器选项 [C++]"
  - "-W1 编译器选项 [C++]"
  - "W2 编译器选项 [C++]"
  - "-W2 编译器选项 [C++]"
  - "W3 编译器选项 [C++]"
  - "-W3 编译器选项 [C++]"
  - "W4 编译器选项 [C++]"
  - "-W4 编译器选项 [C++]"
  - "Wall 编译器选项 [C++]"
  - "-Wall 编译器选项 [C++]"
  - "Warning Level 编译器选项"
  - "警告, 视为错误编译器选项"
  - "wd 编译器选项 [C++]"
  - "-wd 编译器选项 [C++]"
  - "we 编译器选项 [C++]"
  - "-we 编译器选项 [C++]"
  - "wo 编译器选项 [C++]"
  - "-wo 编译器选项 [C++]"
  - "WX 编译器选项 [C++]"
  - "-WX 编译器选项 [C++]"
ms.assetid: d6bc7bf5-c754-4879-909c-8e3a67e2629f
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /w、/Wn、/WX、/Wall、/wln、/wdn、/wen、/won（警告等级）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定编译器如何为给定的编译生成警告。  
  
## 语法  
  
```  
/w  
/Wn  
/WX  
/Wall  
/wln  
/wdn  
/wen  
/won  
```  
  
## 备注  
 下表中描述了这些选项和相关参数。  
  
|选项|说明|  
|--------|--------|  
|**\/w**|禁用所有编译器警告。|  
|**\/W** `n`|指定编译器生成警告的最高等级。  `n` 的有效警告等级范围在 0 到 4 之间：<br /><br /> -   等级 0 禁用所有警告。<br />-   等级 1 显示严重警告。  默认设置为Level1 。<br />-   等级 2 显示所有等级1警告和不如等级1严重的警告。<br />-   等级3显示所有等级 2 的警告和所有其他出于生产目的而建议的警告。<br />-   Level4显示所有等级 3的警告以及信息性警告。  建议您使用此选项。仅提供棉绒的警告。  然而对于新项目，最好在所有编译中使用 `/W4`；解决所有警告将确保难以查找的代码缺陷最少。|  
|**\/Wall**|显示在 \/W4 中未包含 \(示例中，的默认关闭警告的所有 \/W4 警告及所有其他警告。  请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。|  
|**\/WX**|将所有编译器警告都视为错误。  对于新项目，最好在所有编译中使用 **\/WX**；解决所有警告将确保难以查找的代码缺陷最少。<br /><br /> 链接器还有一个 **\/WX** 选项。  有关更多信息，请参见[\/WX（将链接器警告视为错误）](../../build/reference/wx-treat-linker-warnings-as-errors.md)。|  
|**\/w** `ln`|指定特定警告的等级。  第一个参数设置警告等级（与 **\/W**`n` 相同），第二个参数是实际警告编号。<br /><br /> 例如，`/w14326` 使 C4326 生成为等级 1 警告。|  
|**\/wd** `n`|在 `n`指定禁用编译器警告的选项。<br /><br /> 例如，`/wd4326` 禁用编译器警告 C4326。|  
|**\/we** `n`|视为错误在 `n`指定的编译器警告。<br /><br /> 例如，`/we4326` 将警告编号 C4326 标记为错误。|  
|**\/wo** `n`|一次只报告错误在 `n`指定的编译器的警告。<br /><br /> 例如，`/wo4326`将导致警告 C4326 只报告一次。|  
  
 如果用其中一个 **\/w** 选项创建预编译头 \([\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md)\)，任何对此预编译头的使用 \([\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md)\) 将引起那些相同的 **\/w** 选项重新生效。  可以在命令行用另一个 **\/w** 选项通过重写预编译头中的 **\/w** 设置。  
  
 源代码中的杂注指令不受 **\/w** 选项的影响。  
  
 还可以使用 [警告](../../preprocessor/warning.md) 控制在编译时报告警告等级。  
  
 [生成错误文档](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) 描述警告和警告等级，指出某些语句原因可能无法编译，则需要。  
  
### 在Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+**。  
  
3.  在**“常规”**属性页，并修改**“警告等级”**或**“将警告视为错误”**属性。  
  
4.  在**“高级”**属性页，并修改**“禁用特定警告”**属性。  
  
5.  对于其他选项，在**“命令行”**属性页，并在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置编译器选项  
  
-   请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)