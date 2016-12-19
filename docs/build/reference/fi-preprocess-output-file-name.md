---
title: "/Fi（预处理输出文件名） | Microsoft Docs"
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
  - "/Fi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fi 编译器选项 (C++)"
  - "Fi 编译器选项 (C++)"
  - "-Fi 编译器选项 (C++)"
  - "预处理输出文件, 文件名"
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fi（预处理输出文件名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定输出文件的名称，[\/P（预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)编译器选项向其写入预处理的输出。  
  
## 语法  
  
```  
/Fipathname  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`pathname`|**\/P** 编译器选项生成的输出文件的名称和路径。|  
  
## 备注  
 将 **\/Fi** 编译器选项结合 **\/P** 编译器选项使用。  
  
 如果仅指定 `pathname` 参数路径，源文件的基名称将用作预处理的输出文件的基名称。  `pathname` 参数不需要特定的文件扩展名。  但是，扩展名 ".i" 用于未指定文件扩展名的情况。  
  
## 示例  
 以下命令行预处理 PROGRAM.cpp，保留注释，添加 [\#line](../../preprocessor/hash-line-directive-c-cpp.md) 指令，并将结果写入 MYPROCESS.i 文件。  
  
```  
CL /P /FiMYPROCESS.I PROGRAM.CPP  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [\/P（预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)