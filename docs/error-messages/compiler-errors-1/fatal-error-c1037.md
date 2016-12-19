---
title: "错误 C1037 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1037"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1037"
ms.assetid: 79103bca-ccfb-42e7-aef9-9b90c15b162f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1037
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开对象文件的文件名  
  
 无法打开由 [\/Fo](../../build/reference/fo-object-file-name.md) 指定的对象文件。  
  
### 通过检查以下可能的原因进行修复  
  
1.  文件名无效。  
  
2.  内存不足，无法打开该文件。  
  
3.  另一个进程正在使用该文件。  
  
4.  一个只读文件具有相同的名称。  
  
 在 Visual C\+\+ .NET（1300 版本编译器）中，存在一个 Bug：当文件名（或者指向文件名的目录路径）含有 MBCS 字符时，要求正确设置用户区域。 设置系统区域设置是不够的；必须设置用户区域设置以处理 MBCS 字符。