---
title: "Compiler Error C3498 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3498"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3498"
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Compiler Error C3498
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：无法捕获具有托管或 WinRT 类型的变量  
  
 无法在 lambda 中捕获具有托管类型或 Windows 运行时类型的变量。  
  
### 更正此错误  
  
-   将托管或 Windows 运行时变量传递到 lambda 表达式的参数列表。  
  
## 示例  
 下面的示例将生成 C3498，因为 lambda 表达式的捕获列表中出现了具有托管类型的变量：  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## 示例  
 下面的示例通过将托管变量 `s` 传递到 lambda 表达式的参数列表，解决了 C3498：  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)