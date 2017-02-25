---
title: "编译器警告（等级 1）C4674 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4674"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4674"
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 1）C4674
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“方法”应声明为“静态”，而且只能有一个参数  
  
 转换运算符的签名不正确。 该方法不被视为用户定义的转换。  
  
 使用新语法（**\/clr**时，请参阅 [用户定义的运算符](../../dotnet/user-defined-operators-cpp-cli.md) 和 [用户定义的转换](../../dotnet/user-defined-conversions-cpp-cli.md) 了解有关定义运算符的信息。  
  
## 示例  
 下面的示例生成 C4674。  
  
```  
// C4674.cpp // compile with: /clr /WX /W1 /LD ref class G { int op_Implicit(int i) {   // C4674 return 0; } };  
```  
  
## 示例  
 下面的示例生成 C4674。  
  
```  
// C4674_b.cpp // compile with: /clr:oldSyntax /W1 /LD __gc class G { int op_Implicit(int i) {   // C4674 // try the following line instead // static int op_Implicit(int i) { return 0; } };  
```