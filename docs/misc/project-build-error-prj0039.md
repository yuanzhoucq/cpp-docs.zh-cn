---
title: "项目生成错误 PRJ0039 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PRJ0039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0039"
ms.assetid: 207bbc28-922f-44d6-8bdd-3016c850f5b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 项目生成错误 PRJ0039
无法创建临时文件。 为了使 NMake 工具能够运行，必须具备执行此操作的能力。  
  
 生成生成文件项目时（请参阅[创建生成文件项目](../ide/creating-a-makefile-project.md)），Visual C\+\+ 项目系统需要创建一些临时文件。 此错误指示项目系统无法创建一个或多个这些文件。  
  
 TMP 环境变量包含临时目录的名称。  
  
 下面列出了此错误的可能原因以及建议的解决方法：  
  
 用户没有对临时目录的写入访问权限  
 确保你有对临时目录的写入访问权限。  
  
 临时目录中的临时文件太多  
 其他进程可能已创建临时文件，但没有将它们删除。 删除某些或所有这些临时文件。  
  
 无可用磁盘空间  
 删除磁盘上的某些文件或将临时目录更改为具有可用空间的磁盘。  
  
 TMP 环境变量错误  
 很可能是 TMP 环境变量指向的目录不存在。