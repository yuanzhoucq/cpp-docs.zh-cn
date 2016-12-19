---
title: "/Fm（命名映射文件） | Microsoft Docs"
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
  - "/fm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fm 编译器选项 [C++]"
  - "文件 [C++], 创建映射"
  - "Fm 编译器选项 [C++]"
  - "-Fm 编译器选项 [C++]"
  - "映射文件 [C++], 创建链接器"
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fm（命名映射文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通知链接器生成包含段列表的映射文件，并且这些段按照它们在相应的 .exe 文件或 DLL 中出现的顺序排列。  
  
## 语法  
  
```  
/Fmpathname  
```  
  
## 备注  
 默认情况下，此映射文件具有相应 C 或 C\+\+ 源文件的基名称以及 .MAP 扩展名。  
  
 指定 **\/Fm** 的作用与已指定 [\/MAP（生成映射文件）](../../build/reference/map-generate-mapfile.md) 链接器选项时相同。  
  
 如果指定 [\/c（在不链接的情况下进行编译）](../../build/reference/c-compile-without-linking.md) 以取消链接，则 **\/Fm** 无效。  
  
 映射文件中的全局符号通常有一个或多个前导下划线，因为编译器向变量名添加前导下划线。  许多出现在映射文件中的全局符号由编译器和标准库在内部使用。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)