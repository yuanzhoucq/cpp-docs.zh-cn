---
title: "/homeparams（将寄存器参数复制到堆栈） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/homeparams"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/homeparams 编译器选项 [C++]"
  - "-homeparams 编译器选项 [C++]"
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /homeparams（将寄存器参数复制到堆栈）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

强制将传入寄存器的参数写入其在函数入口的堆栈上的位置。  
  
## 语法  
  
```  
/homeparams  
```  
  
## 备注  
 此编译器选项仅适用于 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 编译器（本机编译和跨平台编译）。  
  
 当在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 编译中传递参数时，调用约定要求用于参数的堆栈空间，甚至对于在寄存器中传递的参数也要求。  有关详细信息，请参阅[参数传递](../../build/parameter-passing.md)。  然而，默认情况下，在发布版本中，寄存器参数不会写入已为参数提供的堆栈空间中。  这使得调试程序的优化（发布）版本相当困难。  
  
 对于发布版本，请使用 **\/homeparams** 以确保您可以调试应用程序。  **\/homeparams** 确实意味着性能降低，因为它一定会要求一个时钟周期来将寄存器参数加载到堆栈上。  
  
 在调试版本中，堆栈始终用在寄存器中传递的参数填充。  
  
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