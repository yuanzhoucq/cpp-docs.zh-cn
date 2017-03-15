---
title: "编译器错误 C3699 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3699"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3699"
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3699
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 无法在“type”类型上使用此间接寻址  
  
 不允许在 `type` 上尝试使用间接寻址。  
  
## 示例  
 下面的示例生成 C3699。  
  
```  
// C3699.cpp  
// compile with: /clr /c  
using namespace System;  
int main() {  
   String * s;   // C3699  
   // try the following line instead  
   // String ^ s2;  
}  
```  
  
## 示例  
 trivial 属性不能有引用类型。  有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)。  下面的示例生成 C3699。  
  
```  
// C3699_b.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String % x;   // C3699  
   property System::String ^ y;   // OK  
};  
```  
  
## 示例  
 “pointer to a pointer”语法的等效项是跟踪引用的句柄。  下面的示例生成 C3699。  
  
```  
// C3699_c.cpp  
// compile with: /clr /c  
using namespace System;  
void Test(String ^^ i);   // C3699  
void Test2(String ^% i);  
```