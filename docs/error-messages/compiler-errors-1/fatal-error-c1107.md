---
title: "错误 C1107 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1107"
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能找到程序集“file”: 请使用 \/AI 或通过设置 LIBPATH 环境变量指定程序集搜索路径  
  
 编译器无法定位传递给 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指令的元数据文件。  
  
 [\/AI](../../build/reference/ai-specify-metadata-directories.md) 编译器选项和 `#using` 主题中描述的 LIBPATH 允许指定编译器将在其中查找引用的元数据文件的目录。