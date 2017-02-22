---
title: "/WL（启用单行诊断） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/wl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/WL 编译器选项 [C++]"
  - "WL 编译器选项 [C++]"
  - "-WL 编译器选项 [C++]"
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /WL（启用单行诊断）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将附加信息追加到错误或警告消息之后。  
  
## 语法  
  
```  
/WL  
```  
  
## 备注  
 来自 C\+\+ 编译器的错误和警告消息的后面可以有附加信息，默认情况下这些信息在新行上显示。  当从命令行编译时，附加信息行可以追加到错误或警告消息之后。  在将生成输出捕获到日志文件，然后处理此日志文件以查找所有错误和警告时，这可能是可取的。  由分号将错误或警告消息与附加行隔开。  
  
 并非所有错误和警告消息都有附加信息行。  下面的代码将生成一个具有附加信息行的错误；它将使您可以在使用 **\/WL** 时测试效果。  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
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