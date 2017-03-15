---
title: "编译器警告（等级 1）C4489 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4489"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4489"
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器警告（等级 1）C4489
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“specifier”: 不允许在接口方法“method”上使用；重写说明符只允许在 ref 类和值类方法上使用  
  
 在接口方法上错误使用了说明符关键字。  
  
 有关详细信息，请参阅[重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C4489。  
  
```  
// C4489.cpp  
// compile with: /clr /c /W1  
public interface class I {   
   void f() new;   // C4489  
   virtual void b() override;   // C4489  
  
   void g();   // OK  
};  
```