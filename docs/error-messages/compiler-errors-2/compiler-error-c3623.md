---
title: "编译器错误 C3623 | Microsoft Docs"
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
  - "C3623"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3623"
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3623
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”: 托管或 WinRT 类型中不支持位域  
  
 不允许在托管或 WinRT 类的变量上使用位域。  
  
 以下示例生成 C3623：  
  
```  
// C3623.cpp  
// compile with: /clr  
using namespace System;  
ref class CMyClass {  
public:  
   int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass^ pMyClass = gcnew CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```  
  
 以下示例生成 C3623：  
  
```  
// C3623_2.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__gc class CMyClass {  
   public:  
      int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass *pMyClass = new CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```