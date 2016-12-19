---
title: "编译器警告 C4959 | Microsoft Docs"
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
  - "C4959"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4959"
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4959
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不能在 \/clr:safe 中定义非托管结构“type”，因为访问其成员会产生不可验证的代码  
  
 访问非托管类型的成员会生成无法验证的 \(peverify.exe\) 映像。  
  
 有关详细信息，请参阅[纯代码和可验证代码](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [\/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。  
  
 下面的示例生成 C4959：  
  
```  
// C4959.cpp // compile with: /clr:safe // Uncomment the following line to resolve. // #pragma warning( disable : 4959 ) struct X { int data; }; int main() { X x; x.data = 10;   // C4959 }  
```