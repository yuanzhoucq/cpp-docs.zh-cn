---
title: "/Zc:forScope（强制 for 循环范围中的一致性） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope"
  - "VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope"
  - "/zc:forScope"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 编译器选项 [C++]"
  - "Conformance 编译器选项"
  - "Zc 编译器选项 [C++]"
  - "-Zc 编译器选项 [C++]"
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# /Zc:forScope（强制 for 循环范围中的一致性）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于针对具有 Microsoft 扩展 \([\/Ze](../../cpp/for-statement-cpp.md)\) 的 [for](../../build/reference/za-ze-disable-language-extensions.md) 循环实现标准 C\+\+ 行为。  默认情况下，**\/Zc:forScope** 处于打开状态。  
  
## 语法  
  
```  
/Zc:forScope[-]  
```  
  
## 备注  
 **\/Zc:forScope\-** 选项已弃用，并将从未来版本中删除。 使用 **\/Zc:forScope\-** 将生成弃用警告 D9035。  
  
 标准行为是使 **for** 循环的初始值设定项在 **for** 循环之后超出范围。 在 **\/Zc:forScope\-** 和 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 下，**for** 循环的初始值设定项保持在范围内，直到局部范围结束。  
  
 以下代码在 **\/Ze**（而不是 **\/Za**）下进行编译：  
  
```cpp  
// zc_forScope.cpp  
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp  
// C2065, D9035 expected  
int main() {  
    // Compile by using cl /Zc:forScope- zc_forScope.cpp  
    // to compile this non-standard code as-is.  
    // Uncomment the following line to resolve C2065 for /Za.  
    // int i;  
    for (int i = 0; i < 1; i++)  
        ;  
    i = 20;   // i has already gone out of scope under /Za  
}  
```  
  
 使用 **\/Zc:forScope\-** 时，如果变量由于在上一范围内所作的声明而处在范围内，则将生成警告 C4288（默认关闭）。 为了说明这点，请删除示例代码中用于声明 `int i` 的 `//` 字符。  
  
 可通过使用 [conform](../../preprocessor/conform.md) 杂注修改 **\/Zc:forScope** 的运行时行为。  
  
 如果在包含现有 .pch 文件的项目中使用 **\/Zc:forScope\-**，则将生成警告、忽略 **\/Zc:forScope\-**，并使用现有 .pch 文件继续进行编译。 如果需要生成新的 .pch 文件，请使用 [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md)。  
  
 有关 Visual C\+\+ 中一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在导航窗格中，打开“配置属性”、“C\/C\+\+”、“语言”属性页。  
  
3.  修改**“强制 For 循环范围中的一致性”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)   
 [\/Za、\/Ze（禁用语言扩展）](../../build/reference/za-ze-disable-language-extensions.md)