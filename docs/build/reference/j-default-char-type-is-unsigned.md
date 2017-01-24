---
title: "/J（默认 char 类型是无符号的） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned"
  - "VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned"
  - "/j"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/J 编译器选项 [C++]"
  - "char 数据类型"
  - "默认 char 类型是无符号的"
  - "默认值, char 类型"
  - "J 编译器选项 [C++]"
  - "-J 编译器选项 [C++]"
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /J（默认 char 类型是无符号的）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将默认 `char` 类型从 `signed char` 更改为 `unsigned char`，且在将 `char` 类型扩展到 `int` 类型时为零扩展。  
  
## 语法  
  
```  
/J  
```  
  
## 备注  
 如果将 `char` 值显式声明为`signed`，则**\/J** 选项不会影响它，并且当其扩展为  `int` 类型时，该值将进行符号扩展。  
  
 **\/J** 选项定义 `_CHAR_UNSIGNED`，它在 LIMITS.h 文件中与 `#ifndef` 一起使用以定义默认 `char` 类型的范围。  
  
 ANSI C 和 C\+\+ 并不需要 `char` 类型的特定实现。  该选项在处理最后将翻译为非英语语言的字符数据时很有用。  
  
> [!NOTE]
>  如果您使用ATL\/MFC编译器选项，可能会生成错误。  虽然您可以通过定义 `_ATL_ALLOW_CHAR_UNSIGNED`禁用此错误，此工作区不支持可能不总是起作用。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“属性”**。  
  
2.  在项目的**“属性页”**对话框中，在**“配置属性”**下的左窗格中展开**“C\/C\+\+”**，然后选择**“命令行”**。  
  
3.  在**“附加选项”**窗格中，指定 **\/J** 编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)