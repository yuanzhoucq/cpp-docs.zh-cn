---
title: "@（指定编译器响应文件） | Microsoft Docs"
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
  - "@"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "@ 编译器选项"
  - "cl.exe 编译器, 指定响应文件"
  - "响应文件, C/C++ 编译器"
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# @（指定编译器响应文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定编译器响应文件。  
  
## 语法  
  
```  
@response_file  
```  
  
## Arguments  
 `response_file`  
 包含编译器命令的文本文件。  
  
## 备注  
 响应文件可以包含任何想在命令行上指定的命令。  命令行参数超过 127 个字符时，这会很有用。  
  
 不能从响应文件内部指定 **@** 选项。  即一个响应文件不能嵌入另一个响应文件。  
  
 可以从命令行指定所需数量的响应文件选项（例如 `@respfile.1 @respfile.2`）。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
-   无法从开发环境内部指定响应文件，而必须在命令行上指定。  
  
### 以编程方式设置此编译器选项  
  
-   不能以编程方式更改此编译器选项。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)