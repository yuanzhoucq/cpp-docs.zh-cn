---
title: "编译器警告（等级 1）C4817 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4817"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4817"
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4817
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”：非法使用“.”访问该成员；编译器已将其替换为“\-\>”  
  
 使用了错误的成员访问运算符。  
  
## 示例  
 以下示例生成 C4817：  
  
```  
// C4817.cpp // compile with: /clr /W1 using namespace System; int main() { array<Int32> ^ a = gcnew array<Int32>(100); Console::WriteLine( a.Length );   // C4817 Console::WriteLine( a->Length );   // OK }  
```  
  
## 示例  
 使用 **\/clr:oldSyntax** 也可能生成 C4817。 以下示例生成 C4817：  
  
```  
// C4817_b.cpp // compile with: /clr:oldSyntax /W1 using namespace System; int main() { Int32 a[] = new Int32[11]; Console::WriteLine( a.Length ); // Console::WriteLine( a->Length ); }  
```