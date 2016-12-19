---
title: "编译器错误 CS1906 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1906"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1906"
ms.assetid: 1a6abf5c-f673-4256-93ac-313dce50acc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1906
选项“option”无效；资源可见性必须是“public”或“private”  
  
 此错误表示无效的 [\/resource（将资源文件嵌入到输出文件）](../Topic/-resource%20\(C%23%20Compiler%20Options\).md)或 [\/linkresource（链接到.NET Framework 资源）](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md)命令行选项。 检查 **\/resource** 或 **\/linkresource** 命令行选项的语法，确保使用的可访问性修饰符为 **public** 或 `private`。