---
title: "编译器错误 C3628 | Microsoft Docs"
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
  - "C3628"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3628"
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3628
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“base class”：托管或 WinRT 类只支持公共继承  
  
 试图将托管或 WinRT 类用作[私有](../../cpp/private-cpp.md)或[受保护的](../../cpp/protected-cpp.md)基类。  托管或 WinRT 类只能用作具有[公共](../../cpp/public-cpp.md)访问权限的基类。  
  
 下面的示例生成 C3628，并演示如何修复此错误：  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  
  
 下面的示例生成 C3628，并演示如何修复此错误：  
  
```  
// C3628b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__gc class B {  
};  
  
__gc class D : B {   // C3628, private is the default access level  
  
// The following line resolves the error.  
// __gc class D : public B {  
};  
  
int main() {  
}  
```