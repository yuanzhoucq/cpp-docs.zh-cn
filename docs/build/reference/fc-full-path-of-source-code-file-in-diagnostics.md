---
title: "/FC（所诊断源代码文件的完整路径） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.UseFullPaths"
  - "/FC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FC 编译器选项 [C++]"
  - "-FC 编译器选项 [C++]"
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /FC（所诊断源代码文件的完整路径）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使编译器可以显示在诊断中传递给编译器的源代码文件的完整路径。  
  
## 语法  
  
```  
/FC  
```  
  
## 备注  
 考虑下面的代码示例：  
  
```  
// compiler_option_FC.cpp  
int main( ) {  
   int i   // C2143  
}  
```  
  
 在不使用 **\/FC** 的情况下，诊断文本将与以下诊断文本类似：  
  
-   compiler\_option\_FC.cpp\(5\) : C2143 错误: 语法错误 :“}”前丢失“;”  
  
 在使用 **\/FC** 的情况下，诊断文本将与以下诊断文本类似：  
  
-   c:\\test\\compiler\_option\_FC.cpp\(5\) : C2143 错误: 语法错误 :“}”前丢失“;”  
  
 如果在使用 \_\_FILE\_\_ 宏时要查看文件名的完整路径，也需要 **\/FC**。有关 \_\_FILE\_\_ 的更多信息，请参见 [预定义的宏](../../preprocessor/predefined-macros.md)。  
  
 **\/FC** 选项由 **\/ZI** 暗示。  有关 **\/ZI**的更多信息，请参见[\/Z7、\/Zi、\/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“C\/C\+\+”**节点。  
  
4.  选择**“高级”**属性页。  
  
5.  修改**“使用完整路径”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)