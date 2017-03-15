---
title: "/Fe（命名 EXE 文件） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/fe"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fe 编译器选项 [C++]"
  - "可执行文件, 重命名"
  - "Fe 编译器选项 [C++]"
  - "-Fe 编译器选项 [C++]"
  - "重命名文件编译器选项 [C++]"
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /Fe（命名 EXE 文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为由编译器创建的 .exe 文件或 DLL 指定名称和目录。  
  
## 语法  
  
```  
/Fepathname  
```  
  
## 备注  
 如果不使用此选项，编译器将使用命令行上指定的第一个源文件或对象文件的基名称和扩展名 .exe 或 .dll 为文件提供默认名称。  
  
 如果指定 [\/c（在不链接的情况下进行编译）](../../build/reference/c-compile-without-linking.md) 进行编译但不链接，**\/Fe** 将无效。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“常规”**属性页。  
  
4.  修改**“输出文件”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。  
  
## 示例  
 下列命令行编译并链接当前目录中的所有 C 源文件。  得到的可执行文件被命名为 PROCESS.exe，并且在目录 C:\\BIN 中创建。  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## 示例  
 下列命令行在 `C:\BIN` 中创建一个可执行文件，该文件的基名称与第一个源文件或对象文件的基名称相同：  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)