---
title: "编译器错误 C3409 | Microsoft Docs"
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
  - "C3409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3409"
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3409
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许空特性块  
  
 中括号被编译器解释为[特性](../../windows/cpp-attributes-reference.md)块，但未找到特性。  
  
 如果将方括号用作 lambda 表达式定义的一部分，编译器可能生成此错误。  如果编译器无法确定方括号是 lambda 表达式定义的一部分还是特性块的一部分，则会发生此错误。  有关 lambda 表达式的更多信息，请参见 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。  
  
### 更正此错误  
  
1.  如果方括号是特性块的一部分：  
  
    1.  在特性块中提供一个或多个特性。  
  
    2.  移除特性块。  
  
2.  如果方括号是 lambda 表达式的一部分：  
  
    1.  确保 lambda 表达式遵循有效的语法规则。  
  
         有关 lambda 表达式语法的更多信息，请参见 [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。  
  
## 示例  
 下面的示例会产生 C3409。  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## 示例  
 下面的示例将生成 C3409，因为 lambda 表达式使用 `mutable` 规范，但未提供参数列表。  编译器无法确定方括号是 lambda 表达式定义的一部分还是特性块的一部分。  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## 请参阅  
 [特性](../../windows/cpp-attributes-reference.md)   
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)   
 [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)