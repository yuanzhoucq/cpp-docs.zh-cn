---
title: "/E（预处理到 stdout） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/e"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/E 编译器选项 [C++]"
  - "-E 编译器选项 [C++]"
  - "预处理器输出"
  - "预处理器输出, 复制到 stdout"
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /E（预处理到 stdout）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选项预处理 C 和 C\+\+ 源文件，并将预处理后的文件复制到标准输出设备中。  
  
## 语法  
  
```  
/E  
```  
  
## 备注  
 在此过程中，将执行所有的预处理器指令，执行宏展开，并移除注释。  若要在预处理输出中保留注释，则还请使用 [\/C（在预处理期间保留注释）](../../build/reference/c-preserve-comments-during-preprocessing.md) 编译器选项。  
  
 **\/E** 将 `#line` 指令添加到输出中，添加的位置是每个包含文件的开头和结尾以及被条件编译预处理器指令移除的行的周围。  这些指令将预处理文件中的行重新编号。  因此，在处理后期生成的错误引用原始源文件的行号而不是预处理文件中的行的行号。  
  
 **\/E** 选项会取消编译。  必须重新提交预处理文件以进行编译。  **\/E** 还取消来自 **\/FA**、**\/Fa** 和 **\/Fm** 选项的输出文件。  有关更多信息，请参见[\/FA、\/Fa（列出文件）](../../build/reference/fa-fa-listing-file.md)和[\/Fm（命名映射文件）](../../build/reference/fm-name-mapfile.md)。  
  
 若要取消 `#line` 指令，请改用 [\/EP（不使用 \#line 指令预处理到 stdout）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 选项。  
  
 若要将预处理输出发送到文件而不是 `stdout`，请改用 [\/P（预处理到文件）](../../build/reference/p-preprocess-to-a-file.md) 选项。  
  
 若要取消 `#line` 指令并将预处理输出发送到文件，请同时使用 **\/P** 和 **\/EP**。  
  
 用 **\/E** 选项时，不能使用预编译头。  
  
 请注意，当预处理到单独文件时，不在标记后发出空格。  这可导致非法程序或产生预料不到的副作用。  下面的程序会成功编译：  
  
```  
#define m(x) x  
m(int)main( )  
{  
   return 0;  
}  
```  
  
 然而如果用下列方式编译：  
  
```  
cl -E test.cpp > test2.cpp  
```  
  
 test2.cpp 中的 `int main` 将错误地成为 `intmain`。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## 示例  
 下列命令行预处理 `ADD.C`，保留注释，添加 `#line` 指令，并在标准输出设备上显示结果：  
  
```  
CL /E /C ADD.C  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)