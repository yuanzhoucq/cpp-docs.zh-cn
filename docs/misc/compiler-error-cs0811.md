---
title: "编译器错误 CS0811 | Microsoft Docs"
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
  - "CS0811"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0811"
ms.assetid: 99f81ad3-684f-47aa-adb8-360e24901454
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0811
“name”的完全限定名对于调试信息太长。 请在不使用“\/debug”选项的情况下编译。  
  
 调试信息中的变量和类型名称具有大小约束。  
  
### 更正此错误  
  
1.  如果无法修改名称，则唯一的备用方法是在不使用 [\/debug](../Topic/-debug%20\(C%23%20Compiler%20Options\).md) 选项的情况下编译。  
  
## 示例  
 下面的代码生成 CS0811：  
  
```  
// cs0811.cs //Compile with: /debug using System; using System.Collections.Generic; namespace TestNamespace { using Long = List<List<List<List<List<List<List<List<List<List<List<List<List <List<List<List<List<List<List<List<List<List<List<List<List<List<List<List<int>>>>>>>>>>>>>>>>>>>>>>>>>>>>; // CS0811 class Test { static int Main() { return 1; } } }  
```